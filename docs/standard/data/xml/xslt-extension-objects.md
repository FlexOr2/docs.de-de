---
title: XSLT-Erweiterungsobjekte
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db0d609e4a930a839dae014b597d42aa4499c5ec
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452559"
---
# <a name="xslt-extension-objects"></a>XSLT-Erweiterungsobjekte
Mit Erweiterungsobjekten kann der Funktionsumfang von Stylesheets erweitert werden. Erweiterungsobjekte werden von der <xref:System.Xml.Xsl.XsltArgumentList>-Klasse beibehalten.  
  
 Die Verwendung eines Erweiterungsobjekts bietet gegenüber der Verwendung eines eingebetteten Skripts folgende Vorteile:  
  
-   Sie ermöglicht eine bessere Kapselung und Wiederverwendung von Klassen.  
  
-   Stylesheets werden kleiner und sind besser verwaltbar.  
  
 XSLT-Erweiterungsobjekte werden dem <xref:System.Xml.Xsl.XsltArgumentList>-Objekt mithilfe der <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>-Methode hinzugefügt. Dabei wird ein qualifizierter Name und ein Namespace-URI (Uniform Resource Identifier) mit dem Erweiterungsobjekt verknüpft.  
  
> [!NOTE]
>  Um die <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>-Methode aufzurufen, muss die FullTrust-Berechtigung festgelegt sein. Weitere Informationen finden Sie unter [Codezugriffssicherheit](../../../../docs/framework/misc/code-access-security.md) und [NIB: Benannte Berechtigungssätze](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Von Erweiterungsobjekten kann einer der vier XPath-Grunddatentypen (`number`, `string`, `Boolean` und `node set`) zurückgegeben werden.  
  
 Alle Methoden, die mit dem `params`-Schlüsselwort definiert sind, mit dem eine nicht definierte Anzahl von Parametern übergeben werden kann, werden derzeit nicht von der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse unterstützt. XSLT-Stylesheets, die Methoden mit dem `params`-Schlüsselwort verwenden, funktionieren nicht ordnungsgemäß. Einzelheiten finden Sie unter [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>So verwenden Sie ein XSLT-Erweiterungsobjekt  
  
1.  Erstellen Sie ein <xref:System.Xml.Xsl.XsltArgumentList>-Objekt, und fügen Sie das Erweiterungsobjekt mit der <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>-Methode hinzu.  
  
2.  Rufen Sie das Erweiterungsobjekt aus dem Stylesheet auf.  
  
3.  Übergeben Sie das <xref:System.Xml.Xsl.XsltArgumentList>-Objekt an die <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>-Methode.  
  
## <a name="see-also"></a>Siehe auch

- [XSLT Transformations (XSLT-Transformationen)](../../../../docs/standard/data/xml/xslt-transformations.md)  
- [XSLT-Sicherheitsaspekte](../../../../docs/standard/data/xml/xslt-security-considerations.md)
