---
title: "Programmgesteuertes Arbeiten mit RESX-Dateien | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ressourcendateien, RESX-Dateien"
  - "RESX-Dateien"
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Programmgesteuertes Arbeiten mit RESX-Dateien
Da XML\-Ressourcendateien \(RESX\) aus ordnungsgemäß definiertem XML\-Code bestehen müssen, einschließlich eines Headers, der einem bestimmten Schema entsprechen muss, und auf den Daten in Name\/Wert\-Paaren folgen, werden Sie vermutlich feststellen, dass das manuelle Erstellen dieser Dateien ziemlich fehlerträchtig ist. Alternativ können Sie RESX\-Dateien programmgesteuert mithilfe von Typen und Elementen aus der .NET Framework\-Klassenbibliothek erstellen. Sie können die .NET Framework\-Klassenbibliothek auch zum Abrufen der in RESX\-Dateien gespeicherten Ressourcen verwenden. In diesem Thema wird erläutert, wie Sie die Typen und Elemente im <xref:System.Resources>\-Namespace für das Arbeiten mit RESX\-Dateien verwenden können.  
  
 Beachten Sie, dass dieser Artikel das Arbeiten mit XML\-Dateien \(RESX\) behandelt, die Ressourcen enthalten. Informationen zum Arbeiten mit binären Ressourcendateien, die in Assemblys eingebettet wurden, finden Sie im Thema <xref:System.Resources.ResourceManager>.  
  
> [!WARNING]
>  Es gibt nicht programmgesteuerte Verfahren zum Arbeiten mit RESX\-Dateien. Wenn Sie einem Visual Studio\-Projekt eine Ressourcendatei hinzufügen, stellt Visual Studio eine Oberfläche zum Erstellen und Warten einer RESX\-Datei bereit und konvertiert die RESX\-Datei zum Zeitpunkt der Kompilierung automatisch in eine RESOURCES\-Datei. Ferner können Sie RESX\-Dateien in einem Texteditor direkt bearbeiten. Um eine Beschädigung der Datei zu vermeiden, müssen Sie allerdings sorgfältig darauf achten, keine der in der Datei gespeicherten binären Informationen zu verändern.  
  
## Erstellen einer RESX\-Datei  
 Sie können die Klasse <xref:System.Resources.ResXResourceWriter?displayProperty=fullName> verwenden, um eine RESX\-Datei programmgesteuert zu erstellen, indem Sie folgende Schritte ausführen:  
  
1.  Instanziieren Sie ein <xref:System.Resources.ResXResourceWriter>\-Objekt, indem Sie die <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29?displayProperty=fullName>\-Methode aufrufen und den Namen der RESX\-Datei angeben. Der Dateiname muss die Erweiterung „.resx“ enthalten. Wenn Sie das <xref:System.Resources.ResXResourceWriter>\-Objekt in einem `using`\-Block instanziieren, müssen Sie die Methode <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=fullName> in Schritt 3 nicht explizit aufrufen.  
  
2.  Rufen Sie die <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=fullName>\-Methode für jede Ressource auf, die Sie der Datei hinzufügen möchten. Verwenden Sie die Überladungen dieser Methode, um Zeichenfolgen\-, Objekt\- und binäre Daten \(Bytearray\) hinzuzufügen. Wenn es sich bei der Ressource um ein Objekt handelt, muss es serialisierbar sein.  
  
3.  Rufen Sie die <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=fullName>\-Methode auf, um die Ressourcendatei zu generieren und alle Ressourcen freizugeben. Wenn das <xref:System.Resources.ResXResourceWriter>\-Objekt innerhalb eines `using`\-Blocks erstellt wurde, werden Ressourcen in die RESX\-Datei geschrieben, und die vom <xref:System.Resources.ResXResourceWriter>\-Objekt verwendeten Ressourcen werden am Ende des `using`\-Blocks freigegeben.  
  
 Die resultierende RESX\-Datei weist den entsprechenden Header und ein `data`\-Kennzeichen für jede Ressource auf, die von der <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=fullName>\-Methode hinzugefügt wurde.  
  
> [!WARNING]
>  Verwenden Sie Ressourcendateien nicht, um Kennwörter, sicherheitsrelevante Informationen oder private Daten zu speichern.  
  
 Im folgenden Beispiel wird eine RESX\-Datei mit dem Namen "CarResources.resx" erstellt, mit der sechs Zeichenfolgen, ein Symbol und zwei anwendungsdefinierte Objekte \(zwei `Automobile`\-Objekte\) gespeichert werden. Beachten Sie, dass die Klasse `Automobile`, die im Beispiel definiert und instanziiert wird, mit dem <xref:System.SerializableAttribute>\-Attribut gekennzeichnet ist.  
  
 [!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
 [!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]  
  
> [!IMPORTANT]
>  Sie können auch Visual Studio zum Erstellen von RESX\-Dateien verwenden. Zum Zeitpunkt der Kompilierung verwendet Visual Studio den [Resource File Generator \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md), um die RESX\-Datei in eine binäre Ressourcendatei \(RESOURCES\) zu konvertieren, und bettet sie entweder in eine Anwendungsassembly oder in eine Satellitenassembly ein.  
  
 Eine RESX\-Datei kann nicht in eine von der Laufzeitumgebung ausführbare Datei eingebettet oder in eine Satellitenassembly kompiliert werden. Sie müssen die RESX\-Datei mithilfe des [Resource File Generator \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) in eine binäre Ressourcendatei \(RESOURCES\) konvertieren. Die resultierende RESOURCES\-Datei kann dann in eine Anwendungsassembly oder eine Satellitenassembly eingebettet werden. Weitere Informationen finden Sie unter [Erstellen von Ressourcendateien](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md).  
  
## Aufzählen von Ressourcen  
 In bestimmten Fällen müssen anstelle einer bestimmten alle Ressourcen aus einer RESX\-Datei abgerufen werden. Zu diesem Zweck können Sie die Klasse <xref:System.Resources.ResXResourceReader?displayProperty=fullName> verwenden, die einen Enumerator für alle in der RESX\-Datei enthaltenen Ressourcen enthält. Die <xref:System.Resources.ResXResourceReader?displayProperty=fullName>\-Klasse implementiert <xref:System.Collections.IDictionaryEnumerator>, der ein <xref:System.Collections.DictionaryEntry>\-Objekt zurückgibt, das für jede Iteration der Schleife eine bestimmte Ressource darstellt. Seine <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=fullName>\-Eigenschaft gibt den Schlüssel der Ressource und seine <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=fullName>\-Eigenschaft den Wert der Ressource zurück.  
  
 Im folgenden Beispiel wird ein <xref:System.Resources.ResXResourceReader>\-Objekt für die im vorhergehenden Beispiel erstellte Datei „CarResources.resx“ erstellt, das durch die Ressourcendatei iteriert. Es fügt die zwei in der Ressourcendatei definierten `Automobile`\-Objekte einem <xref:System.Collections.Generic.List%601?displayProperty=fullName> und fünf der sechs Zeichenfolgen einem <xref:System.Collections.SortedList>\-Objekt hinzu. Die Werte in dem <xref:System.Collections.SortedList>\-Objekt werden in ein Parameterarray konvertiert, das zum Anzeigen von Spaltenüberschriften in der Konsole verwendet wird. Die Werte der Eigenschaft `Automobile` werden ebenfalls in der Konsole angezeigt.  
  
 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]  
  
## Abrufen einer bestimmten Ressource  
 Über das Aufzählen der Elemente in einer RESX\-Datei hinaus können Sie mithilfe der <xref:System.Resources.ResXResourceSet?displayProperty=fullName>\-Klasse eine bestimmte Ressource anhand des Namens abrufen. Die <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=fullName>\-Methode ruft den Wert einer benannten Zeichenfolgenressource ab. Die <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=fullName>\-Methode ruft den Wert eines benannten Objekts oder Binärdaten ab. Die Methode gibt ein Objekt zurück, für das anschließend eine Umwandlung \(in C\#\) oder Konvertierung \(in Visual Basic\) in ein Objekt des geeigneten Typs erfolgen muss.  
  
 Im folgenden Beispiel wird die Überschriftenzeichenfolge eines Formulars und dessen Symbol anhand des Ressourcennamens abgerufen. Außerdem werden die von der Anwendung definierten `Automobile`\-Objekte abgerufen, die im vorherigen Beispiel verwendet wurden, und in einem <xref:System.Windows.Forms.DataGridView>\-Steuerelement angezeigt.  
  
 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]  
  
## Konvertieren von RESX\-Dateien in binäre RESOURCES\-Dateien  
 Das Konvertieren von RESX\-Dateien in eingebettete binäre Ressourcendateien \(RESOURCES\) bietet erhebliche Vorteile. Obwohl RESX\-Dateien in der Entwicklungsphase einer Anwendung leicht zu lesen und zu verwalten sind, sind sie nur selten in den fertigen Anwendungen enthalten. Wenn sie als Teil einer Anwendung verteilt werden, liegen sie als separate Dateien vor, getrennt von der ausführbaren Programmdatei und ihren begleitenden Bibliotheken. Im Unterschied dazu sind RESOURCES\-Dateien in die ausführbare Programmdatei oder ihre begleitenden Assemblys eingebettet. Außerdem wird beim Einsatz von RESX\-Dateien zur Laufzeit bei lokalisierten Anwendungen der Entwickler für die Behandlung des Ressourcenfallbacks in die Pflicht genommen. Wenn demgegenüber eine Sammlung von Satellitenassemblys erstellt wurde, die eingebettete RESOURCES\-Dateien enthalten, übernimmt die Common Language Runtime die Zuständigkeit für den Ressourcenfallbackvorgang.  
  
 Zum Konvertieren einer RESX\-Datei in eine RESOURCES\-Datei wird der [Resource File Generator \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) verwendet, der die folgende grundlegende Syntax aufweist:  
  
 **Resgen.exe** *.resxDateiname*  
  
 Das Ergebnis ist eine binäre Ressourcendatei, die den gleichen Stammdateinamen wie die RESX\-Datei und darüber hinaus eine RESOURCES\-Dateierweiterung aufweist. Diese Datei kann dann zum Zeitpunkt der Kompilierung in eine ausführbare Datei oder eine Bibliothek kompiliert werden. Wenn Sie den Visual Basic\-Compiler verwenden, verwenden Sie die folgende Syntax, um eine RESOURCES\-Datei in die ausführbare Programmdatei einer Anwendung einzubetten:  
  
 **vbc** *Dateiname* **.vb \/resource:** *.resourcesDateiname*  
  
 Wenn Sie C\# verwenden, lautet die Syntax wie folgt:  
  
 **csc** *Dateiname* **.cs \/resource:** *.resourcesDateiname*  
  
 Die RESOURCES\-Datei kann mithilfe von [Assembly Linker \(AL.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) auch in eine Satellitenassembly eingebettet werden. Dafür gilt diese Syntax:  
  
 **al** *RESOURCESDateiname* **\/out:** *AssemblyDateiname*  
  
## Siehe auch  
 [Erstellen von Ressourcendateien](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)   
 [Resgen.exe \(Resource File Generator\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)   
 [Al.exe \(Assembly Linker\-Tool\)](../../../docs/framework/tools/al-exe-assembly-linker.md)