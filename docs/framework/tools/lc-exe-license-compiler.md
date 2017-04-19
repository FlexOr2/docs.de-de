---
title: "Lc.exe (License Compiler) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Lc.exe"
  - ".licx file"
  - "License Compiler"
  - "control licenses [Windows Forms]"
  - "compiling licenses file"
  - "license file"
  - ".licenses file"
  - "Windows Forms, control licenses"
  - "licensed controls [Windows Forms]"
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Lc.exe (License Compiler)
Der Lizenzcompiler liest Textdateien mit Informationen über die Lizenzierung und erstellt eine Binärdatei, die als Ressource in eine ausführbare Datei der Common Language Runtime eingebettet werden kann.  
  
 Eine LICX\-Textdatei wird vom Windows Forms\-Designer automatisch generiert oder aktualisiert, sobald dem Formular ein lizenziertes Steuerelement hinzugefügt wird.  Bei der Kompilierung wandelt das Projektsystem die LICX\-Textdatei in eine binäre LICENSES\-Ressource um, die die Lizenzierung des .NET\-Steuerelements unterstützt.  Die binäre Ressource wird anschließend in die Projektausgabe eingebettet.  
  
 Kreuzkompilierung zwischen 32\-Bit und 64\-Bit wird nicht unterstützt, wenn Sie beim Erstellen des Projekts den Lizenzcompiler verwenden.  Das liegt daran, dass der Lizenzcompiler Assemblys laden muss und das Laden von 64\-Bit\-Assemblys aus einer 32\-Bit\-Anwendung und umgekehrt nicht erlaubt ist.  Verwenden Sie in diesem Fall den Lizenzcompiler von der Befehlszeile aus, um die Lizenz manuell zu kompilieren, und geben Sie die entsprechende Architektur an.  
  
 Dieses Tool wird automatisch mit Visual Studio installiert.  Zum Ausführen des Tools verwenden Sie die Developer\-Eingabeaufforderung \(oder die Visual Studio\-Eingabeaufforderung in Windows 7\).  Weitere Informationen finden Sie unter [Eingabeaufforderungen](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Geben Sie an der Eingabeaufforderung Folgendes ein:  
  
## Syntax  
  
```  
  
        lc /target:  
        targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Option|Beschreibung|  
|------------|------------------|  
|**\/complist:** *filename*|Gibt den Namen einer Datei an, die die Liste der lizenzierten Komponenten enthält, die in die LICENSES\-Datei eingebunden werden sollen.  Auf die einzelnen Komponenten wird mit dem vollständigen Namen verwiesen, wobei pro Zeile jeweils nur eine Komponente aufgeführt wird.<br /><br /> Benutzer der Befehlszeile können für jedes Formular des Projekts eine eigene Datei angeben.  "Lc.exe" akzeptiert mehrere Eingabedateien und erstellt eine einzige LICENSES\-Datei.|  
|**\/h**\[**elp**\]|Zeigt Befehlssyntax und Optionen für das Tool an.|  
|**\/i:** *module*|Gibt die Module an, die die in der Datei **\/complist** aufgelisteten Komponenten enthalten.  Verwenden Sie mehrere **\/i**\-Flags, um mehrere Module anzugeben.|  
|**\/nologo**|Unterdrückt die Anzeige des Startbanners von Microsoft.|  
|**\/outdir:** *path*|Gibt das Verzeichnis an, in dem die LICENSES\-Ausgabedatei gespeichert werden soll.|  
|**\/target:** *targetPE*|Gibt die ausführbare Datei an, für die die LICENSES\-Datei generiert wird.|  
|**\/v**|Gibt den ausführlichen Modus an und zeigt Statusinformationen zur Kompilierung an.|  
|**@** *Datei*|Gibt die Antwortdatei \(.rsp\) an.|  
|**\/?**|Zeigt Befehlssyntax und Optionen für das Tool an.|  
  
## Beispiel  
  
1.  Wenn Sie das lizenzierte Steuerelement `MyCompany.Samples.LicControl1` verwenden, das in der `Samples.DLL` in einer Anwendung namens `HostApp.exe`enthalten ist, können Sie die Datei `HostAppLic.txt` mit folgendem Inhalt erstellen.  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2.  Erstellen Sie die LICENSES\-Datei `HostApp.exe.licenses` mit dem folgenden Befehl.  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3.  Erstellen Sie `HostApp.exe` mit der LICENSES\-Datei als Ressource.  Wenn Sie eine C\#\-Anwendung erstellt haben, erstellen Sie die Anwendung mit dem folgenden Befehl.  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Mit dem folgenden Befehl wird `myApp.licenses` aus den von `hostapplic.txt`, `hostapplic2.txt` und `hostapplic3.txt` angegebenen Listen lizenzierter Komponenten kompiliert.  Das `modulesList`\-Argument gibt die Module mit den lizenzierten Komponenten an.  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## Beispiel für eine Antwortdatei  
 Die folgende Auflistung enthält ein Beispiel für eine Antwortdatei namens `response.rsp`.  Weitere Informationen zu Antwortdateien finden Sie unter [Response Files](../Topic/MSBuild%20Response%20Files.md).  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
  
```  
  
 Die folgende Befehlszeile verwendet die Datei `response.rsp`.  
  
```  
lc @response.rsp  
```  
  
## Siehe auch  
 [Tools](../../../docs/framework/tools/index.md)   
 [Al.exe \(Assembly Linker\-Tool\)](../../../docs/framework/tools/al-exe-assembly-linker.md)   
 [Eingabeaufforderungen](../../../docs/framework/tools/developer-command-prompt-for-vs.md)