---
title: "Entfernen des vom Designer zu einer XAML-Datei hinzugef&#252;gten Ansichtzustands | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Entfernen des vom Designer zu einer XAML-Datei hinzugef&#252;gten Ansichtzustands
Dieses Beispiel veranschaulicht, wie eine Klasse erstellt wird, die von <xref:System.Windows.Markup.XamlWriter> abgeleitet wird, und entfernt den Ansichtszustand aus einer XAML\-Datei.[!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] schreibt Informationen in das XAML\-Dokument, das als Ansichtszustand bezeichnet wird.Der Ansichtszustand bezieht sich auf die Informationen, die während der Entwurfszeit erforderlich sind, z. B. die Layoutpositionierung, jedoch nicht zur Laufzeit.[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] fügt diese Informationen in das XAML\-Dokument ein, während es bearbeitet wird.[!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] schreibt den Ansichtszustand in der XAML\-Datei mit dem `mc:Ignorable`\-Attribut. Daher werden diese Informationen nicht geladen, wenn die Laufzeit die XAML\-Datei lädt.In diesem Beispiel wird veranschaulicht, wie eine Klasse erstellt wird, mit der diese Ansichtszustandsinformationen bei der Verarbeitung von XAML\-Knoten entfernt werden.  
  
## Diskussion  
 In diesem Beispiel wird veranschaulicht, wie ein benutzerdefinierter Writer erstellt wird.  
  
 Zum Erstellen eines benutzerdefinierten XAML\-Writers müssen Sie eine Klasse erstellen, die von <xref:System.Windows.Markup.XamlWriter> erbt.Da XAML\-Writer häufig geschachtelt werden, wird in der Regel ein "innerer" XAML\-Writer nachverfolgt.Diese "inneren" Writer können als Verweis auf den verbleibenden Stapel XAML\-Writer angesehen werden, sodass Sie über mehrere Einstiegspunkte verfügen und die Verarbeitung des restlichen Stapels delegieren können.  
  
 In diesem Beispiel gibt es einige relevante Elemente.Eines ist die Überprüfung, ob das geschriebene Element aus einem Designernamespace stammt.Beachten Sie, dass dies die Verwendung anderer Typen des Designernamespace in einem Workflow nicht mehr ermöglicht.  
  
```  
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)  
{  
return xamlMember.IsAttachable &&  
   xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);  
}  
  
const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";  
The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.  
public ViewStateCleaningWriter(XamlWriter innerWriter)  
{  
this.InnerWriter = innerWriter;  
this.MemberStack = new Stack<XamlMember>();  
}  
  
XamlWriter InnerWriter {get; set; }  
Stack<XamlMember> MemberStack {get; set; }  
  
```  
  
 Hierdurch wird auch ein Stapel von XAML\-Membern erstellt, die beim Durchlaufen des Knotenstreams verwendet werden.Die verbleibende Arbeit dieses Beispiels ist zum größten Teil in der <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>\-Methode enthalten.  
  
```  
public override void WriteStartMember(XamlMember xamlMember)  
{  
MemberStack.Push(xamlMember);  
if (IsDesignerAttachedProperty(xamlMember))  
{  
m_attachedPropertyDepth++;  
}  
  
if (m_attachedPropertyDepth > 0)  
{  
return;  
}  
  
InnerWriter.WriteStartMember(xamlMember);  
}  
  
```  
  
 Nachfolgende Methoden können überprüfen, ob sie immer noch in einem Ansichtszustandscontainer enthalten sind. Wenn dies der Fall ist, können sie zurückkehren und den Knoten nicht im Writerstapel weiter übergeben.  
  
```  
public override void WriteValue(Object value)  
{  
if (m_attachedPropertyDepth > 0)  
{  
return;  
}  
  
InnerWriter.WriteValue(value);  
}  
```  
  
 Um einen benutzerdefinierten XAML\-Writer verwenden zu können, müssen Sie ihn in einem Stapel XAML\-Writer verketten.Der folgende Code zeigt diese Verwendung.  
  
```  
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };  
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);  
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());  
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);  
  
```  
  
#### So verwenden Sie dieses Beispiel  
  
1.  Öffnen Sie mit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] die ViewStateCleaningWriter.sln\-Projektmappendatei.  
  
2.  Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu dem Verzeichnis, in dem ViewStageCleaningWriter.exe erstellt wird.  
  
3.  Führen Sie ViewStateCleaningWriter.exe für die Datei Workflow1.xaml aus.  
  
     Die Syntax für die ausführbare Datei ist im folgenden Beispiel dargestellt.  
  
 **ViewStateCleaningWriter.exe \[Eingabedatei\] \[Ausgabedatei\]**     Hierdurch erfolgt die Ausgabe einer XAML\-Datei in \[Ausgabedatei\], aus der alle Ansichtszustandsinformationen entfernt wurden.  
  
    > [!NOTE]
    >  Für einen <xref:System.Activities.Statements.Sequence>\-Workflow wird eine Reihe von Virtualisierungshinweisen entfernt.Dies veranlasst den Designer, das Layout beim nächsten Laden neu zu berechnen.Wenn Sie dieses Beispiel für ein <xref:System.Activities.Statements.Flowchart> verwenden, werden alle Positionierungs\- und Zeilenroutinginformationen entfernt. Bei nachfolgendem Laden in den Designer werden alle Aktivitäten auf der linken Seite des Bildschirms gestapelt.  
  
#### So erstellen Sie eine Beispiel\-XAML\-Datei zur Verwendung mit diesem Beispiel  
  
1.  Öffnen Sie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  So erstellen Sie eine neue Workflowkonsolenanwendung.  
  
3.  Legen Sie einige Aktivitäten in der Entwurfsfläche ab.  
  
4.  Speichern Sie die Workflow\-XAML\-Datei.  
  
5.  Überprüfen Sie die XAML\-Datei auf die Eigenschaften, die dem Ansichtszustand zugeordnet sind.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert.Überprüfen Sie das folgende \(standardmäßige\) Verzeichnis, bevor Sie fortfahren.  
>   
>  `<Installationslaufwerk>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation \(WCF\) and Windows Workflow Foundation \(WF\) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]\- und [!INCLUDE[wf1](../../../../includes/wf1-md.md)]\-Beispiele herunterzuladen.Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`  
  
## Siehe auch