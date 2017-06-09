---
title: "Unterst&#252;tzende Token | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
caps.latest.revision: 29
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 29
---
# Unterst&#252;tzende Token
Im Beispiel für unterstützende Token wird veranschaulicht, wie einer Nachricht, die WS\-Sicherheit verwendet, zusätzliche Token hinzugefügt werden.  Das Beispiel fügt zusätzlich zu einem Sicherheitstoken für den Benutzernamen ein binäres X.509\-Sicherheitstoken hinzu.  Das Token wird in einem WS\-Sicherheit\-Nachrichtenkopf vom Client zum Dienst übergeben, und ein Teil der Nachricht wird mit dem privaten Schlüssel signiert, der dem X.509\-Sicherheitstoken zugeordnet ist, um dem Empfänger den Besitz des X.509\-Zertifikats nachzuweisen.  Dies ist nützlich, wenn die Anforderung besteht, dass einer Nachricht mehrere Ansprüche zugeordnet sein müssen, um den Absender zu authentifizieren oder zu autorisieren.  Der Dienst implementiert einen Vertrag, der ein Anforderungs\-Antwort\-Kommunikationsmuster definiert.  
  
## Veranschaulicht  
 Dieses Beispiel veranschaulicht Folgendes:  
  
-   Wie ein Client zusätzliche Sicherheitstoken an einen Dienst übergeben kann.  
  
-   Wie der Server auf zusätzlichen Sicherheitstoken zugeordnete Ansprüche zugreifen kann.  
  
-   Wie das X.509\-Zertifikat des Servers dazu verwendet wird, den zur Nachrichtenverschlüsselung und für die Signatur verwendeten symmetrischen Schlüssel zu schützen.  
  
> [!NOTE]
>  Die Setupprozedur und die Buildanweisungen für dieses Beispiel befinden sich am Ende dieses Themas.  
  
## Client wird mit Benutzernamentoken und dem unterstützenden X.509\-Sicherheitstoken authentifiziert  
 Der Dienst macht einen einzelnen Endpunkt für die Kommunikation verfügbar, der programmgesteuert mithilfe der `BindingHelper`\-Klasse und der `EchoServiceHost`\-Klasse erstellt wird.  Der Endpunkt besteht aus einer Adresse, einer Bindung und einem Vertrag.  Die Bindung wird mit einer benutzerdefinierten Bindung unter Verwendung von `SymmetricSecurityBindingElement` und `HttpTransportBindingElement` konfiguriert.  In diesem Beispiel wird `SymmetricSecurityBindingElement` so eingestellt, dass es ein X.509\-Zertifikat für den Dienst verwendet, um den symmetrischen Schlüssel während der Übertragung zu schützen und um in einem WS\-Sicherheit\-Nachrichtenkopf zusammen mit dem unterstützenden `UserNameToken` ein `X509SecurityToken` zu übergeben.  Der symmetrische Schlüssel wird verwendet, um den Nachrichtentext und das Sicherheitstoken für den Benutzernamen zu verschlüsseln.  Das unterstützende Token wird im WS\-Sicherheit\-Nachrichtenkopf als zusätzliches binäres Sicherheitstoken übergeben.  Der Nachweis für die Authentizität des unterstützenden Tokens wird durch Signieren eines Teils der Nachricht mit dem privaten Schlüssel erbracht, der dem unterstützenden X.509\-Sicherheitstoken zugeordnet ist.  
  
```  
public static Binding CreateMultiFactorAuthenticationBinding()  
{  
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();  
  
    // the message security binding element will be configured to require 2 tokens:  
    // 1) A username-password encrypted with the service token  
    // 2) A client certificate used to sign the message  
  
    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)  
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();  
  
    // Create supporting token parameters for the client X509 certificate.  
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();  
    // Specify that the supporting token is passed in message send by the client to the service  
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;  
    // Turn off derived keys  
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;  
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message  
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);  
  
    // Create a CustomBinding based on the constructed security binding element.  
    return new CustomBinding(messageSecurity, httpTransport);  
}  
  
```  
  
 Das Verhalten legt die Dienstanmeldeinformationen fest, die zur Clientauthentifizierung verwendet werden sollen, sowie Informationen über das X.509\-Zertifikat des Diensts.  Im Beispiel wird `CN=localhost` als Betreffname im X.509\-Zertifikat für den Dienst verwendet.  
  
```  
override protected void InitializeRuntime()  
{  
    // Extract the ServiceCredentials behavior or create one.  
    ServiceCredentials serviceCredentials =   
        this.Description.Behaviors.Find<ServiceCredentials>();  
    if (serviceCredentials == null)  
    {  
        serviceCredentials = new ServiceCredentials();  
        this.Description.Behaviors.Add(serviceCredentials);  
    }  
  
    // Set the service certificate  
    serviceCredentials.ServiceCertificate.SetCertificate(  
                                       "CN=localhost");  
  
/*  
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).  
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.  
*/  
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
  
    // Create the custom binding and add an endpoint to the service.  
    Binding multipleTokensBinding =  
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
    this.AddServiceEndpoint(typeof(IEchoService),   
                          multipleTokensBinding, string.Empty);  
    base.InitializeRuntime();  
}  
```  
  
 Dienstcode:  
  
```  
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]  
public class EchoService : IEchoService  
{  
    public string Echo()  
    {  
        string userName;  
        string certificateSubjectName;  
        GetCallerIdentities(  
            OperationContext.Current.ServiceSecurityContext,   
            out userName,   
            out certificateSubjectName);  
            return String.Format("Hello {0}, {1}",   
                    userName, certificateSubjectName);  
    }  
  
    public void Dispose()  
    {  
    }  
  
    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,   
            string claimType, out TClaimResource resourceValue)  
            where TClaimResource : class  
    {  
        resourceValue = default(TClaimResource);  
        IEnumerable<Claim> matchingClaims =   
            claimSet.FindClaims(claimType, Rights.PossessProperty);  
        if(matchingClaims == null)  
            return false;  
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
        if (enumerator.MoveNext())  
        {  
            resourceValue =   
              (enumerator.Current.Resource == null) ? null :   
              (enumerator.Current.Resource as TClaimResource);  
            return true;  
        }  
        else  
        {  
            return false;  
        }  
    }  
  
    // Returns the username and certificate subject name provided by   
    //the client  
    void GetCallerIdentities(ServiceSecurityContext   
        callerSecurityContext,   
        out string userName, out string certificateSubjectName)  
    {  
        userName = null;  
        certificateSubjectName = null;  
  
       // Look in all the claimsets in the authorization context  
       foreach (ClaimSet claimSet in   
               callerSecurityContext.AuthorizationContext.ClaimSets)  
       {  
            if (claimSet is WindowsClaimSet)  
            {  
                // Try to find a Name claim. This will have been   
                // generated from the windows username.  
                string tmpName;  
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                      out tmpName))  
                {  
                    userName = tmpName;  
                }  
            }  
            else if (claimSet is X509CertificateClaimSet)  
            {  
                // Try to find an X500DisinguishedName claim. This will   
                // have been generated from the client certificate.  
                X500DistinguishedName tmpDistinguishedName;  
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
                               ClaimTypes.X500DistinguishedName,   
                               out tmpDistinguishedName))  
                {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
                }  
            }  
        }  
    }  
}   
```  
  
 Der Clientendpunkt wird auf ähnliche Weise wie der Dienstendpunkt konfiguriert.  Der Client verwendet die gleiche `BindingHelper`\-Klasse, um eine Bindung zu erstellen.  Der Rest des Setups befindet sich in der `Client`\-Klasse.  Der Client legt Informationen über das Sicherheitstoken für den Benutzernamen und das unterstützende X.509\-Sicherheitstoken sowie Informationen über das X.509\-Zertifikat für den Dienst im Setupcode für die Auflistung der Clientendpunkt\-Verhaltensweisen fest.  
  
```  
 static void Main()  
 {  
     // Create the custom binding and an endpoint address for   
     // the service.  
     Binding multipleTokensBinding =   
         BindingHelper.CreateMultiFactorAuthenticationBinding();  
         EndpointAddress serviceAddress = new EndpointAddress(  
         "http://localhost/servicemodelsamples/service.svc");  
       ChannelFactory<IEchoService> channelFactory = null;  
       IEchoService client = null;  
  
       Console.WriteLine("Username authentication required.");  
       Console.WriteLine(  
         "Provide a valid machine or domain account. [domain\\user]");  
       Console.WriteLine("   Enter username:");  
       string username = Console.ReadLine();  
       Console.WriteLine("   Enter password:");  
       string password = "";  
       ConsoleKeyInfo info = Console.ReadKey(true);  
       while (info.Key != ConsoleKey.Enter)  
       {  
           if (info.Key != ConsoleKey.Backspace)  
           {  
               if (info.KeyChar != '\0')  
               {  
                   password += info.KeyChar;  
                }  
                info = Console.ReadKey(true);  
            }  
            else if (info.Key == ConsoleKey.Backspace)  
            {  
                if (password != "")  
                {  
                    password =   
                       password.Substring(0, password.Length - 1);  
                }  
                info = Console.ReadKey(true);  
            }  
         }  
         for (int i = 0; i < password.Length; i++)  
            Console.Write("*");  
         Console.WriteLine();  
         try  
         {  
           // Create a proxy with the previously create binding and   
           // endpoint address  
              channelFactory =   
                 new ChannelFactory<IEchoService>(  
                     multipleTokensBinding, serviceAddress);  
           // configure the username credentials, the client   
           // certificate and the server certificate on the channel   
           // factory   
           channelFactory.Credentials.UserName.UserName = username;  
           channelFactory.Credentials.UserName.Password = password;  
           channelFactory.Credentials.ClientCertificate.SetCertificate(  
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);  
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(  
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);  
           client = channelFactory.CreateChannel();  
           Console.WriteLine("Echo service returned: {0}",   
                                           client.Echo());  
  
           ((IChannel)client).Close();  
           channelFactory.Close();  
        }  
        catch (CommunicationException e)  
        {  
         Abort((IChannel)client, channelFactory);  
         // if there is a fault then print it out  
         FaultException fe = null;  
         Exception tmp = e;  
         while (tmp != null)  
         {  
            fe = tmp as FaultException;  
            if (fe != null)  
            {  
                break;  
            }  
            tmp = tmp.InnerException;  
        }  
        if (fe != null)  
        {  
           Console.WriteLine("The server sent back a fault: {0}",   
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);  
        }  
        else  
        {  
         Console.WriteLine("The request failed with exception: {0}",e);  
        }  
    }  
    catch (TimeoutException)  
    {  
        Abort((IChannel)client, channelFactory);  
        Console.WriteLine("The request timed out");  
    }  
    catch (Exception e)  
    {  
         Abort((IChannel)client, channelFactory);  
          Console.WriteLine(  
          "The request failed with unexpected exception: {0}", e);  
    }  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
## Anzeigen von Aufruferinformationen  
 Um die Informationen zu den Aufrufern anzuzeigen, können Sie `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` verwenden, wie im folgenden Code gezeigt.  `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` enthält dem aktuellen Aufrufer zugeordnete Autorisierungsansprüche.  Jene Ansprüche werden automatisch von [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] für jedes in der Nachricht empfangene Token angegeben.  
  
```  
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string   
                         claimType, out TClaimResource resourceValue)  
    where TClaimResource : class  
{  
    resourceValue = default(TClaimResource);  
    IEnumerable<Claim> matchingClaims =   
    claimSet.FindClaims(claimType, Rights.PossessProperty);  
    if (matchingClaims == null)  
          return false;  
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();  
    if (enumerator.MoveNext())  
    {  
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);  
        return true;  
    }  
    else  
    {  
         return false;  
    }  
}  
  
// Returns the username and certificate subject name provided by the client  
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)  
{  
    userName = null;  
    certificateSubjectName = null;  
  
    // Look in all the claimsets in the authorization context  
    foreach (ClaimSet claimSet in   
      callerSecurityContext.AuthorizationContext.ClaimSets)  
    {  
        if (claimSet is WindowsClaimSet)  
        {  
            // Try to find a Name claim. This will have been generated   
            //from the windows username.  
            string tmpName;  
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,   
                                                     out tmpName))  
            {  
                userName = tmpName;  
            }  
        }  
        else if (claimSet is X509CertificateClaimSet)  
         {  
            //Try to find an X500DisinguishedName claim.   
            //This will have been generated from the client   
            //certificate.  
            X500DistinguishedName tmpDistinguishedName;  
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,   
               ClaimTypes.X500DistinguishedName,   
               out tmpDistinguishedName))  
            {  
                    certificateSubjectName = tmpDistinguishedName.Name;  
            }  
        }  
    }  
}  
```  
  
## Ausführen des Beispiels  
 Wenn Sie das Beispiel ausführen, fordert der Client Sie zuerst auf, den Benutzernamen und das Kennwort für das Benutzernamentoken anzugeben.  Vergewissern Sie sich, dass Sie die korrekten Werte zu Ihrem Systemkonto angeben, da [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auf dem Dienst die im Benutzernamentoken bereitgestellten Werte der vom System bereitgestellten Identität zuordnet.  Danach zeigt der Client die Antwort vom Dienst an.  Drücken Sie im Clientfenster die EINGABETASTE, um den Client zu schließen.  
  
## Setupbatchdatei  
 Mit der in diesem Beispiel enthaltenen Batchdatei Setup.bat können Sie den Server mit relevanten Zertifikaten zum Ausführen einer von Internetinformationsdiensten \(IIS\) gehosteten Anwendung konfigurieren, die serverzertifikatbasierte Sicherheit erfordert.  Diese Batchdatei muss so geändert werden, dass sie computerübergreifend oder in einem nicht gehosteten Fall funktioniert.  
  
 Nachfolgend erhalten Sie einen kurzen Überblick über die verschiedenen Abschnitte der Batchdateien, damit Sie sie so ändern können, dass sie in der entsprechenden Konfiguration ausgeführt werden.  
  
### Erstellen des Clientzertifikats  
 Die folgenden Zeilen aus der Batchdatei Setup.bat erstellen das zu verwendende Clientzertifikat.  Die `%CLIENT_NAME%`\-Variable gibt den Betreff des Clientzertifikats an.  In diesem Beispiel wird "client.com" als Betreffname verwendet.  
  
 Das Zertifikat wird im persönlichen Speicher unter dem Speicherort `CurrentUser` gespeichert.  
  
```  
echo ************  
echo making client cert  
echo ************  
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
```  
  
### Installieren des Clientzertifikats im vertrauenswürdigen Speicher des Servers  
 Die folgende Zeile in der Batchdatei Setup.bat kopiert das Clientzertifikat in den Serverspeicher für vertrauenswürdige Personen.  Dieser Schritt ist erforderlich, da das Serversystem von Makecert.exe generierten Zertifikaten nicht implizit vertraut.  Wenn Sie bereits über ein Zertifikat verfügen, dass von einem vertrauenswürdigen Clientstammzertifikat abstammt \(z. B. ein von Microsoft ausgegebenes Zertifikat\), ist dieser Schritt zum Auffüllen des Clientzertifikatspeichers mit dem Serverzertifikat nicht erforderlich.  
  
```  
echo ************  
echo copying client cert to server's CurrentUserstore  
echo ************  
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople  
```  
  
### Erstellen des Serverzertifikats  
 Mit den folgenden Zeilen aus der Batchdatei "Setup.bat" wird das zu verwendende Serverzertifikat erstellt.  Die Variable `%SERVER_NAME%`  gibt den Servernamen an.  Ändern Sie diese Variable, und geben Sie Ihren eigenen Servernamen an.  Standardmäßig lautet die Variable in dieser Batchdatei localhost.  
  
 Das Zertifikat wird im persönlichen Speicher unter dem Speicherort LocalMachine gespeichert.  Das Zertifikat wird für die IIS\-gehosteten Dienste im LocalMachine\-Speicher gespeichert.  Für selbst gehostete Dienste sollten Sie die Batchdatei so ändern, dass das Serverzertifikat im Speicherort CurrentUser gespeichert wird. Ersetzen Sie hierzu die Zeichenfolge LocalMachine durch CurrentUser.  
  
```  
echo ************  
echo Server cert setup starting  
echo %SERVER_NAME%  
echo ************  
echo making server cert  
echo ************  
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
```  
  
### Installieren des Serverzertifikats im Clientspeicher für vertrauenswürdige Zertifikate  
 Mit den folgenden Zeilen in der Batchdatei Setup.bat wird das Serverzertifikat in den Clientspeicher für vertrauenswürdige Personen kopiert.  Dieser Schritt ist erforderlich, da von "Makecert.exe" generierte Zertifikate nicht implizit vom Clientsystem als vertrauenswürdig eingestuft werden.  Wenn Sie bereits über ein Zertifikat verfügen, dass von einem vertrauenswürdigen Clientstammzertifikat abstammt \(z. B. ein von Microsoft ausgegebenes Zertifikat\), ist dieser Schritt zum Auffüllen des Clientzertifikatspeichers mit dem Serverzertifikat nicht erforderlich.  
  
```  
echo ************  
echo copying server cert to client's TrustedPeople store  
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
```  
  
### Aktivieren des Zugriffs auf den privaten Schlüssel des Zertifikats  
 Um den Zugriff vom IIS\-gehosteten Dienst aus auf den privaten Schlüssel des Zertifikats zu aktivieren, müssen dem Benutzerkonto, unter dem der IIS\-gehostete Prozess ausgeführt wird, entsprechende Berechtigungen für den privaten Schlüssel gewährt werden.  Dies wird durch die letzten Schritte im Skript Setup.bat erreicht.  
  
```  
echo ************  
echo setting privileges on server certificates  
echo ************  
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
iisreset  
```  
  
##### So können Sie das Beispiel einrichten, erstellen und ausführen  
  
1.  Stellen Sie sicher, dass Sie die [Einmaliges Setupverfahren für Windows Communication Foundation\-Beispiele](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) ausgeführt haben.  
  
2.  Befolgen Sie zum Erstellen der Projektmappe die Anweisungen unter [Erstellen der Windows Communication Foundation\-Beispiele](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Um das Beispiel in einer Konfiguration mit einem Computer oder computerübergreifend auszuführen, folgen Sie den folgenden Anweisungen.  
  
##### So führen Sie das Beispiel auf demselben Computer aus  
  
1.  Öffnen Sie eine [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]\-Eingabeaufforderung mit Administratorrechten, und führen Sie Setup.bat aus dem Beispielinstallationsordner aus.  Hiermit werden alle Zertifikate installiert, die zum Ausführen des Beispiels erforderlich sind.  
  
    > [!NOTE]
    >  Die Batchdatei Setup.bat ist darauf ausgelegt, an einer [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]\-Eingabeaufforderung ausgeführt zu werden.  Die innerhalb der [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]\-Eingabeaufforderung festgelegte PATH\-Umgebungsvariable zeigt auf das Verzeichnis mit den ausführbaren Dateien, die für das Skript Setup.bat erforderlich sind.  Entfernen Sie nach Abschluss des Beispiels unbedingt die Zertifikate, indem Sie Cleanup.bat ausführen.  In anderen Sicherheitsbeispielen werden die gleichen Zertifikate verwendet.  
  
2.  Starten Sie Client.exe aus dem Ordner \\client\\bin.  In der Clientkonsolenanwendung wird Clientaktivität angezeigt.  
  
3.  Wenn der Client und der Dienst nicht miteinander kommunizieren können, finden Sie weitere Informationen unter [Tipps zur Problembehandlung](http://msdn.microsoft.com/de-de/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### So führen Sie das Beispiel computerübergreifend aus  
  
1.  Erstellen Sie auf dem Dienstcomputer ein Verzeichnis.  Erstellen Sie mithilfe des Verwaltungstools für Internetinformationsdienste \(IIS\) für dieses Verzeichnis eine virtuelle Anwendung namens "servicemodelsamples".  
  
2.  Kopieren Sie die Dienstprogrammdateien aus \\inetpub\\wwwroot\\servicemodelsamples in das virtuelle Verzeichnis auf dem Dienstcomputer.  Stellen Sie sicher, dass Sie die Dateien in das Unterverzeichnis \\bin kopieren.  Kopieren Sie außerdem die Dateien Setup.bat, Cleanup.bat und ImportClientCert.bat auf den Dienstcomputer.  
  
3.  Erstellen Sie auf dem Clientcomputer ein Verzeichnis für die Clientbinärdateien.  
  
4.  Kopieren Sie die Clientprogrammdateien in das Clientverzeichnis auf dem Clientcomputer.  Kopieren Sie die Dateien "Setup.bat", "Cleanup.bat" und "ImportServiceCert.bat" ebenfalls auf den Client.  
  
5.  Führen Sie auf dem Server `setup.bat service` an einer Visual Studio\-Eingabeaufforderung mit Administratorrechten aus.  Durch Ausführen von `setup.bat` `` mit dem Argument `service` wird ein Dienstzertifikat mit dem vollqualifizierten Domänennamen des Computers erstellt und in die Datei "Service.cer" exportiert.  
  
6.  Bearbeiten Sie die Datei "Web.config" so, dass sie den neuen Zertifikatnamen \(im `findValue`\-Attribut im serviceCertificate\-Element von [\<serviceCertificate\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)\) enthält. Dieser entspricht dem vollqualifizierten Domänennamen des Computers.  
  
7.  Kopieren Sie die Datei Service.cer aus dem Dienstverzeichnis in das Clientverzeichnis auf dem Clientcomputer.  
  
8.  Führen Sie auf dem Client `setup.bat client` an einer Visual Studio\-Eingabeaufforderung mit Administratorrechten aus.  Durch Ausführen von `setup.bat` mit dem Argument `client` wird ein Clientzertifikat mit dem Namen client.com erstellt und in die Datei Client.cer exportiert.  
  
9. Ändern Sie in der Datei "Client.exe.config" auf dem Clientcomputer den Wert für die Adresse des Endpunkts so, dass er mit der neuen Adresse Ihres Diensts übereinstimmt.  Ersetzen Sie dazu localhost durch den vollqualifizierten Domänennamen des Servers.  
  
10. Kopieren Sie die Datei Client.cer aus dem Clientverzeichnis in das Dienstverzeichnis auf dem Server.  
  
11. Führen Sie auf dem Client "ImportServiceCert.bat" aus.  Dadurch wird das Dienstzertifikat aus der Datei Service.cer in den Speicher CurrentUser – TrustedPeople importiert.  
  
12. Führen Sie auf dem Server "ImportClientCert.bat" aus. Dadurch wird das Clientzertifikat von der Datei "Client.cer" in den LocalMachine &\#8211; TrustedPeople\-Speicher importiert.  
  
13. Starten Sie auf dem Clientcomputer Client.exe in einem Eingabeaufforderungsfenster.  Wenn der Client und der Dienst nicht miteinander kommunizieren können, finden Sie weitere Informationen unter [Tipps zur Problembehandlung](http://msdn.microsoft.com/de-de/8787c877-5e96-42da-8214-fa737a38f10b).  
  
##### So stellen Sie den Zustand vor Ausführung des Beispiels wieder her  
  
-   Führen Sie Cleanup.bat im Beispielordner aus, nachdem Sie das Beispiel fertig ausgeführt haben.  
  
> [!NOTE]
>  Wenn dieses Beispiel computerübergreifend ausgeführt wird, entfernt dieses Skript keine Dienstzertifikate auf einem Client.  Wenn Sie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]\-Beispiele ausgeführt haben, die Zertifikate computerübergreifend verwenden, müssen Sie die Dienstzertifikate entfernen, die im Speicher CurrentUser \- TrustedPeople installiert wurden.  Verwenden Sie dazu den folgenden Befehl: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Beispiel: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## Siehe auch