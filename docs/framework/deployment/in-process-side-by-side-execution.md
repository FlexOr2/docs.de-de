---
title: Prozessinterne parallele Ausführung
ms.date: 03/30/2017
helpviewer_keywords:
- in-process side-by-side execution
- side-by-side execution, in-process
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ee5f223d5e92d9a60776df6bf2108a4fd14b9e0f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195202"
---
# <a name="in-process-side-by-side-execution"></a>Prozessinterne parallele Ausführung
Ab [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] können Sie mit prozessinternem parallelem Hosting mehrere Versionen der Common Language Runtime (CLR) in einem einzelnen Prozess ausführen. Standardmäßig werden verwaltete COM-Komponenten mit der .NET Framework-Version ausgeführt, mit der sie erstellt wurden, unabhängig von der .NET Framework-Version, die für den Prozess geladen wird.  
  
## <a name="background"></a>Hintergrund  
 Das .NET Framework bot schon immer paralleles Hosting für verwaltete Codeanwendungen, vor [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] gab es diese Funktion jedoch nicht für verwaltete COM-Komponenten. In der Vergangenheit wurden verwaltete COM-Komponenten, die in einen Prozess geladen wurden, entweder mit der Version der bereits geladenen Runtime oder mit der neuesten installierten Version von .NET Framework ausgeführt. Wenn diese Version nicht mit der COM-Komponente kompatibel war, ist die Komponente fehlgeschlagen.  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] bietet eine neue Herangehensweise des parallelen Hostings, wodurch Folgendes sichergestellt werden kann:  
  
-   Die Installation einer neuen Version von .NET Framework hat keinen Einfluss auf vorhandene Anwendungen.  
  
-   Anwendungen werden auf der Version des .NET Framework aufgeführt, mit dem sie erstellt wurden. Sie verwenden nicht die neue Version des .NET Framework, es sei denn, es wird ausdrücklich darauf hingewiesen. Es ist für Anwendungen, zu der ein Übergang stattfindet, jedoch einfacher, eine neue Version von .NET Framework zu verwenden.  
  
## <a name="effects-on-users-and-developers"></a>Auswirkungen auf Benutzer und Entwickler  
  
-   **Endbenutzer und Systemadministratoren**. Diese Benutzer können nun bei der Installation einer Version der Runtime sicherer sein, wenn sie diese entweder eigenständig oder mit einer Anwendung erstellen. Dies hat keinen Einfluss auf deren Computer. Vorhandene Anwendungen werden genauso wie vorher ausgeführt.  
  
-   **Anwendungsentwickler**. Das parallele Hosting hat so gut wie keine Auswirkungen auf Anwendungsentwickler. Standardmäßig werden Anwendungen immer auf der Version des .NET Framework ausgeführt, auf dem sie erstellt wurden; dies hat sich nicht verändert. Jedoch können Entwickler dieses Verhalten außer Kraft setzen und Anwendungen dazu bringen, unter einer neueren Version des .NET Framework zu laufen (siehe [Szenario 2](#scenarios)).  
  
-   **Bibliotheksentwickler und Consumer**. Das parallele Hosting löst nicht die Probleme mit der Kompatibilität, denen Bibliotheksentwickler gegenüberstehen. Eine Bibliothek, die direkt durch eine Anwendung geladen wird, entweder durch einen Direktverweis oder einen <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>-Aufruf, verwendet weiterhin die Runtime von <xref:System.AppDomain>, in der sie geladen wurde. Sie sollten Ihre Bibliotheken für alle .NET Framework-Versionen testen, die Sie unterstützen möchten. Wenn eine Anwendung mithilfe der [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]-Runtime kompiliert wird, jedoch eine Bibliothek enthält, die mit einer früheren Runtime erstellt wurde, wird dies Bibliothek ebenso die [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]-Runtime verwenden. Wenn Sie jedoch über eine Anwendung verfügen, die mithilfe einer früheren Runtime erstellt wurde, sowie eine Bibliothek, die mit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] erstellt wurde, müssen Sie Ihre Anwendung dazu zwingen, auch [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] zu verwenden (siehe [Szenario 3](#scenarios)).  
  
-   **Entwickler verwalteter COM-Komponenten**. Früher wurden die verwalteten COM-Komponenten automatisch mithilfe der aktuellsten Version der Runtime ausgeführt, die auf dem Computer installiert war. Sie können nun COM-Komponenten für die Version der Runtime ausführen, mit der sie erstellt wurden.  
  
     So wie in der folgenden Tabelle gezeigt, können Komponenten, die mit der .NET Framework-Version 1.1 erstellt wurden, parallel mit Komponenten der Version 4 ausgeführt werden. Sie können jedoch nicht mit Komponenten der Version 2.0, 3.0 oder 3.5 ausgeführt werden, da das parallele Hosting für diese Versionen nicht verfügbar ist.  
  
    |.NET Framework-Version|1.1|2.0 - 3.5|4|  
    |----------------------------|---------|----------------|-------|  
    |1.1|Nicht zutreffend|Nein|Ja|  
    |2.0 - 3.5|Nein|Nicht zutreffend|Ja|  
    |4|Ja|Ja|Nicht zutreffend|  
  
> [!NOTE]
>  .NET Framework-Versionen 3.0 und 3.5 werden inkrementell auf Version 2.0 erstellt und müssen nicht parallel ausgeführt werden. Sie sind an und für sich dieselbe Version.  
  
<a name="scenarios"></a>   
## <a name="common-side-by-side-hosting-scenarios"></a>Häufige Szenarios des parallelen Hostings  
  
-   **Szenario 1:** Native Anwendung, die COM-Komponenten verwendet, die mit früheren Versionen von .NET Framework erstellt wurden.  
  
     Installierte .NET Framework-Versionen: Die [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] und alle anderen Versionen des .NET Framework, die von den COM-Komponenten verwendet werden.  
  
     Das muss ich tun: In diesem Szenario unternehmen Sie nichts. Die COM-Komponenten werden mit der Version des .NET Framework ausgeführt, mit der sie registriert wurden.  
  
-   **Szenario 2**: Verwaltete Anwendung, die mit [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] erstellt wurde, die lieber mit [!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)] ausgeführt werden soll, jedoch auch unter [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ausgeführt werden kann, wenn Version 2.0 nicht verfügbar ist.  
  
     Installierte .NET Framework-Version: Eine frühere Version von .NET Framework und [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
     Vorgehensweise: Verwenden Sie in der [Anwendungskonfigurationsdatei](../../../docs/framework/configure-apps/index.md) im Anwendungsverzeichnis das [\<startup>-Element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) und das [\<supportedRuntime>-Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md), die wie folgt festgelegt sind:  
  
    ```xml  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   **Szenario 3:** Native Anwendung, die COM-Komponenten verwendet, die mit früheren Versionen von .NET Framework erstellt wurden, die Sie mit [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ausführen möchten.  
  
     Installierte .NET Framework-Versionen: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]  
  
     Vorgehensweise: Verwenden Sie in der Anwendungskonfigurationsdatei im Anwendungsverzeichnis das `<startup>`-Element, mit mit dem `useLegacyV2RuntimeActivationPolicy`-Attribut, das auf `true` festgelegt ist, sowie das `<supportedRuntime>`-Element, das wie folgt festgelegt ist:  
  
    ```xml  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel stellt einen nicht verwalteten COM-Host dar, der eine verwaltete COM-Komponente mithilfe der Version von .NET Framework ausführt, für deren Verwendung die Komponente kompiliert wurde.  
  
 Um das folgende Beispiel auszuführen, kompilieren und registrieren Sie die folgende verwaltete COM-Komponente mithilfe von [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]. Um die Komponente zu registrieren, klicken Sie im **Projekt**-Menü auf **Eigenschaften**, auf die Registerkarte **Erstellen**, und aktivieren Sie dann das Kontrollkästchen **Für COM-Interop registrieren**.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 Kompilieren Sie die folgende nicht verwaltete C++-Anwendung, die das COM-Objekt aktiviert, das durch das vorherige Beispiel erstellt wurde.  
  
```  
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");   
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
- [\<startup>-Element](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
- [\<supportedRuntime> Element](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
