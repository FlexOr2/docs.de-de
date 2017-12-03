---
title: Implementierung des XSLT-Prozessors durch die XslTransform-Klasse
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 167cd81ecbc25ca243e3b4a7a6aa7327679528e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="d6bf8-102">Implementierung des XSLT-Prozessors durch die XslTransform-Klasse</span><span class="sxs-lookup"><span data-stu-id="d6bf8-102">XslTransform Class Implements the XSLT Processor</span></span>
> [!NOTE]
>  <span data-ttu-id="d6bf8-103">Die <xref:System.Xml.Xsl.XslTransform>-Klasse ist in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] veraltet.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="d6bf8-104">Mithilfe der <xref:System.Xml.Xsl.XslCompiledTransform>-Klasse können Sie XSLT-Transformationen (Extensible Stylesheet Language for Transformations) vornehmen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d6bf8-105">Finden Sie unter [mithilfe der Klasse "XslCompiledTransform"](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) und [Migrieren von der XslTransform-Klasse](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-105">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="d6bf8-106">Die <xref:System.Xml.Xsl.XslTransform>-Klasse ist ein XSLT-Prozessor, der die W3C-Empfehlung zu XSL-Transformationen (XSLT), Version 1.0, implementiert.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="d6bf8-107">Die <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methode wird zum Auffinden und Lesen von Stylesheets verwendet, und mit der <xref:System.Xml.Xsl.XslTransform.Transform%2A>-Methode wird das angegebene Quelldokument umgewandelt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="d6bf8-108">Jeder Speicher, der die Schnittstelle <xref:System.Xml.XPath.IXPathNavigable> implementiert, kann als Quelldokument für <xref:System.Xml.Xsl.XslTransform> dienen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="d6bf8-109">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] implementiert gegenwärtig die <xref:System.Xml.XPath.IXPathNavigable>-Schnittstelle für das <xref:System.Xml.XmlDocument>, das <xref:System.Xml.XmlDataDocument> und das <xref:System.Xml.XPath.XPathDocument>. Diese können daher alle als Eingabequelldokumente für eine Transformation verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-109">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>  
  
 <span data-ttu-id="d6bf8-110">Das <xref:System.Xml.Xsl.XslTransform>-Objekt in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] unterstützt nur die XSLT 1.0-Spezifikation, die mit dem folgenden Namespace definiert sind:</span><span class="sxs-lookup"><span data-stu-id="d6bf8-110">The <xref:System.Xml.Xsl.XslTransform> object in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">    
```  
  
 <span data-ttu-id="d6bf8-111">Das Stylesheet kann mithilfe der <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methode aus einer der folgenden Klassen geladen werden:</span><span class="sxs-lookup"><span data-stu-id="d6bf8-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>  
  
-   <span data-ttu-id="d6bf8-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="d6bf8-112">XPathNavigator</span></span>  
  
-   <span data-ttu-id="d6bf8-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="d6bf8-113">XmlReader</span></span>  
  
-   <span data-ttu-id="d6bf8-114">Einer Zeichenfolge, die eine URL darstellt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-114">A string representing a URL</span></span>  
  
 <span data-ttu-id="d6bf8-115">Für jede der zuvor aufgeführten Eingabeklassen ist eine unterschiedliche <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methode vorhanden.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="d6bf8-116">Manche Methoden nehmen eine Kombination einer dieser Klassen und der <xref:System.Xml.XmlResolver>-Klasse als Argumente an.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="d6bf8-117"><xref:System.Xml.XmlResolver> wird zum Auffinden von Ressourcen verwendet, auf die mit `<xsl:import>` oder `<xsl:include>` im Stylesheet verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="d6bf8-118">Die folgenden Methoden akzeptieren eine Zeichenfolge, <xref:System.Xml.XmlReader> oder <xref:System.Xml.XPath.XPathNavigator> als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>  
  
```vb  
Overloads Public Sub Load(String)  
```  
  
```csharp  
public void Load(string);  
```  
  
```vb  
Overloads Public Sub Load(String, XmlResolver)  
```  
  
```csharp  
public void Load(string, XmlResolver);  
```  
  
```vb  
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XmlReader, XmlResolver, Evidence);  
```  
  
```vb  
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)  
```  
  
```csharp  
public void Load(XPathNavigator, XmlResolver, Evidence);  
```  
  
 <span data-ttu-id="d6bf8-119">Die meisten der oben aufgeführten <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methoden akzeptieren einen <xref:System.Xml.XmlResolver> als Parameter.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="d6bf8-120"><xref:System.Xml.XmlResolver> wird zum Laden des Stylesheets und ggf. zum Laden weiterer Stylesheets verwendet, auf die im xsl:import-Element und im xsl:include-Element verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>  
  
 <span data-ttu-id="d6bf8-121">Die meisten der <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methoden akzeptieren auch einen Evidence-Parameter.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="d6bf8-122">Der Evidence-Parameter ist als <xref:System.Security.Policy.Evidence> mit dem Stylesheet verknüpft.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="d6bf8-123">Die Sicherheitsebene des Stylesheets beeinflusst die Sicherheitsebene aller nachfolgenden Ressourcen, auf die es verweist, z. B. das enthaltene Skript, alle verwendeten `document()`-Funktionen und alle von <xref:System.Xml.Xsl.XsltArgumentList> verwendeten Erweiterungsobjekte.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="d6bf8-124">Wenn das Stylesheet mithilfe einer <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methode geladen wird, die zwar einen URL-Parameter, aber keinen Evidence-Parameter enthält, wird der Beweis des Stylesheets berechnet, indem die gegebene URL mit der jeweiligen Site und Zone kombiniert wird.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>  
  
 <span data-ttu-id="d6bf8-125">Wenn weder URI noch Evidence bereitgestellt werden, gilt der für das Stylesheet festgelegte Evidence als vollständig vertrauenswürdig.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="d6bf8-126">Laden Sie Stylesheets ausschließlich von vertrauenswürdigen Quellen, und fügen Sie <xref:System.Xml.Xsl.XsltArgumentList> niemals Erweiterungsobjekte hinzu, die nicht vertrauenswürdig sind.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
 <span data-ttu-id="d6bf8-127">Weitere Informationen zu Sicherheitsstufen und beweisen und wie er wirkt sich auf scripting finden Sie unter [Skripting mithilfe von XSLT-Stylesheet \<msxsl: SCRIPT >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span><span class="sxs-lookup"><span data-stu-id="d6bf8-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="d6bf8-128">Informationen zu Sicherheitsstufen und Beweis und den Auswirkungen der Erweiterungsobjekte finden Sie unter ["XsltArgumentList" für Stylesheetparameter und Erweiterungsobjekte](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span><span class="sxs-lookup"><span data-stu-id="d6bf8-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>  
  
 <span data-ttu-id="d6bf8-129">Informationen zu Sicherheitsstufen und beweisen und wie er wirkt sich auf die `document()` funktionieren, finden Sie unter [Auflösen von externen XSLT-Stylesheets und Dokumenten](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span><span class="sxs-lookup"><span data-stu-id="d6bf8-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).</span></span>  
  
 <span data-ttu-id="d6bf8-130">Ein Stylesheet kann mit einer Reihe von Eingabeparametern ausgestattet werden.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="d6bf8-131">Das Stylesheet kann auch Funktionen für Erweiterungsobjekte aufrufen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="d6bf8-132">Sowohl Parameter als auch Erweiterungsobjekte werden dem Stylesheet mithilfe der <xref:System.Xml.Xsl.XsltArgumentList>-Klasse bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="d6bf8-133">Weitere Informationen zum <xref:System.Xml.Xsl.XsltArgumentList> finden Sie unter <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>  
  
## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="d6bf8-134">Empfehlungen für die sichere Verwendung der XslTransform-Klasse</span><span class="sxs-lookup"><span data-stu-id="d6bf8-134">Recommended Secure Use of XslTransform Class</span></span>  
 <span data-ttu-id="d6bf8-135">Die Sicherheitsberechtigungen des Stylesheets hängen davon ab, welcher Beweistyp bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="d6bf8-136">Die folgende Tabelle fasst den Speicherort des Stylesheets zusammen und beschreibt den bereitzustellenden Beweistyp.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>  
  
-   <span data-ttu-id="d6bf8-137">Für das XSLT-Stylesheet sind keine externen Verweise vorhanden, oder das Stylesheet stammt aus einer vertrauenswürdigen Codebasis.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>  
  
    -   <span data-ttu-id="d6bf8-138">Stellen Sie den Beweis aus der Assembly bereit:</span><span class="sxs-lookup"><span data-stu-id="d6bf8-138">Provide the evidence from your assembly:</span></span>  
  
         `Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)`  
  
         `XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);`  
  
-   <span data-ttu-id="d6bf8-139">Das XSLT-Stylesheet stammt aus einer externen Quelle.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d6bf8-140">Der Ursprung der Quelle ist bekannt, und es ist ein überprüfbarer URI vorhanden.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-140">The origin of the source is known and there is a verifiable URI.</span></span>  
  
    -   <span data-ttu-id="d6bf8-141">Verwenden Sie den URI zum Erstellen des Beweises.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-141">Create evidence using the URI.</span></span>  
  
         `Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)`  
  
         `XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);`  
  
-   <span data-ttu-id="d6bf8-142">Das XSLT-Stylesheet stammt aus einer externen Quelle.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d6bf8-143">Der Ursprung der Quelle ist unbekannt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-143">The origin of the source is not known.</span></span>  
  
    -   <span data-ttu-id="d6bf8-144">Legen Sie den Beweis auf `null` fest.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-144">Set evidence to `null`.</span></span> <span data-ttu-id="d6bf8-145">Skriptblöcke werden nicht verarbeitet, die XSLT-Funktion `document()` wird nicht unterstützt, und privilegierte Erweiterungsobjekte sind nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>  
  
         <span data-ttu-id="d6bf8-146">Zusätzlich können Sie den `resolver`-Parameter auf `null` setzen. Dadurch wird sichergestellt, dass `xsl:import`- und `xsl:include`-Elemente nicht verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>  
  
-   <span data-ttu-id="d6bf8-147">Das XSLT-Stylesheet stammt aus einer externen Quelle.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="d6bf8-148">Der Ursprung der Quelle ist unbekannt, aber die Skriptunterstützung wird benötigt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-148">The origin of the source is not known, but you require script support.</span></span>  
  
    -   <span data-ttu-id="d6bf8-149">Fordern Sie einen Beweis vom Aufrufer an.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-149">Request evidence from the caller.</span></span>  
  
## <a name="transformation-of-xml-data"></a><span data-ttu-id="d6bf8-150">Transformation von XML-Daten</span><span class="sxs-lookup"><span data-stu-id="d6bf8-150">Transformation of XML Data</span></span>  
 <span data-ttu-id="d6bf8-151">Nach dem Laden eines Stylesheets wird die Transformation gestartet, indem eine der <xref:System.Xml.Xsl.XslTransform.Transform%2A>-Methoden aufgerufen und ein Eingabequelldokument bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="d6bf8-152">Die <xref:System.Xml.Xsl.XslTransform.Transform%2A>-Methode ist überladen, sodass unterschiedliche Transformationsausgaben möglich sind..</span><span class="sxs-lookup"><span data-stu-id="d6bf8-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="d6bf8-153">Die Transformation kann zu folgenden Ausgabeformaten führen:</span><span class="sxs-lookup"><span data-stu-id="d6bf8-153">The transformation can result in the following output formats:</span></span>  
  
-   <xref:System.Xml.XmlReader>  
  
-   <xref:System.Xml.XmlWriter>  
  
-   <xref:System.IO.TextWriter>  
  
-   <xref:System.IO.Stream>  
  
-   <span data-ttu-id="d6bf8-154">Zeichenfolgen-URL der Datei</span><span class="sxs-lookup"><span data-stu-id="d6bf8-154">String URL of file</span></span>  
  
 <span data-ttu-id="d6bf8-155">Das letzte Format, die Zeichenfolgen-URL, ermöglicht ein häufig vorkommendes Szenario, bei dem ein in einer URL befindliches Eingabedokument transformiert und dann in die Ausgabe-URL geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="d6bf8-156">Diese <xref:System.Xml.Xsl.XslTransform.Transform%2A> -Methode ist eine bequeme Methode zum Laden eines XML-Dokuments aus einer Datei, zum Durchführen der XSL-Transformation und zum Schreiben der Ausgabe in eine Datei.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="d6bf8-157">Dadurch wird verhindert, dass Sie das Eingabequelldokument erstellen und laden und dann in einen Dateistream schreiben müssen.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="d6bf8-158">Das folgende Codebeispiel veranschaulicht die Verwendung der <xref:System.Xml.Xsl.XslTransform.Transform%2A>-Methode mit der Zeichenfolgen-URL als Eingabe und Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="d6bf8-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>  
  
```vb  
Dim xsltransform As XslTransform = New XslTransform()  
xsltransform.Load("favorite.xsl")  
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)  
```  
  
```csharp  
XslTransform xsltransform = new XslTransform();  
xsltransform.Load("favorite.xsl");  
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);  
```  
  
## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="d6bf8-159">Transformieren eines Abschnitts eines XML-Dokuments</span><span class="sxs-lookup"><span data-stu-id="d6bf8-159">Transforming a Section of an XML Document</span></span>  
 <span data-ttu-id="d6bf8-160">Transformationen werden auf das gesamte Dokument angewendet.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="d6bf8-161">Wenn Sie einen anderen Knoten als den Stammknoten des Dokuments übergeben, wird dadurch nicht verhindert, dass im Transformationsprozess auf alle Knoten im geladenen Dokument zugegriffen wird.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="d6bf8-162">Zum Transformieren eines Ergebnisstrukturfragments müssen Sie ein <xref:System.Xml.XmlDocument> erstellen, das nur das Ergebnisstrukturfragment enthält, und dieses <xref:System.Xml.XmlDocument> an die <xref:System.Xml.Xsl.XslTransform.Transform%2A>-Methode übergeben.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="d6bf8-163">Im folgenden Beispiel wird eine Transformation für ein Ergebnisstrukturfragment durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-163">The following example performs a transformation on a result tree fragment.</span></span>  
  
```vb  
Dim xslt As New XslTransform()  
xslt.Load("print_root.xsl")  
Dim doc As New XmlDocument()  
doc.Load("library.xml")  
' Create a new document containing just the result tree fragment.  
Dim testNode As XmlNode = doc.DocumentElement.FirstChild  
Dim tmpDoc As New XmlDocument()  
tmpDoc.LoadXml(testNode.OuterXml)  
' Pass the document containing the result tree fragment   
' to the Transform method.  
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))  
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)  
```  
  
```csharp  
XslTransform xslt = new XslTransform();       
xslt.Load("print_root.xsl");  
XmlDocument doc = new XmlDocument();  
doc.Load("library.xml");  
// Create a new document containing just the result tree fragment.  
XmlNode testNode = doc.DocumentElement.FirstChild;   
XmlDocument tmpDoc = new XmlDocument();   
tmpDoc.LoadXml(testNode.OuterXml);  
// Pass the document containing the result tree fragment   
// to the Transform method.  
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");  
xslt.Transform(tmpDoc, null, Console.Out, null);  
```  
  
 <span data-ttu-id="d6bf8-164">Im Beispiel werden die Datei library.xml und die Datei print_root.xsl als Eingabe verwendet, und es wird Folgendes auf der Konsole ausgegeben:</span><span class="sxs-lookup"><span data-stu-id="d6bf8-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console.</span></span>  
  
```  
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl   
Root node is book.  
```  
  
 <span data-ttu-id="d6bf8-165">library.xml</span><span class="sxs-lookup"><span data-stu-id="d6bf8-165">library.xml</span></span>  
  
```xml  
<library>  
  <book genre='novel' ISBN='1-861001-57-5'>  
     <title>Pride And Prejudice</title>  
  </book>  
  <book genre='novel' ISBN='1-81920-21-2'>  
     <title>Hook</title>  
  </book>  
</library>  
```  
  
 <span data-ttu-id="d6bf8-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="d6bf8-166">print_root.xsl</span></span>  
  
```xml  
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >  
  <output method="text" />   
  <template match="/">  
     Root node is  <value-of select="local-name(//*[position() = 1])" />   
  </template>  
</stylesheet>  
```  
  
## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="d6bf8-167">XSLT-Migration von .NET Framework, Version 1.0, auf .NET Framework, Version 1.1</span><span class="sxs-lookup"><span data-stu-id="d6bf8-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>  
 <span data-ttu-id="d6bf8-168">In der folgenden Tabelle werden die veralteten [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-Methoden, Version 1.0, und neue [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-Methoden, Version 1.1, für die <xref:System.Xml.Xsl.XslTransform.Load%2A>-Methode gezeigt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-168">The following table shows the obsolete [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0 methods and new [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="d6bf8-169">Mithilfe der neuen Methoden können Sie die Berechtigungen für das Stylesheet einschränken, indem Sie Beweise angeben.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>  
  
|<span data-ttu-id="d6bf8-170">Veraltete Load-Methoden in .NET Framework Version 1.0</span><span class="sxs-lookup"><span data-stu-id="d6bf8-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="d6bf8-171">Ersatz Load-Methoden in .NET Framework Version 1.1</span><span class="sxs-lookup"><span data-stu-id="d6bf8-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|  
|------------------------------------------------------|---------------------------------------------------------|  
|<span data-ttu-id="d6bf8-172">Load(XPathNavigator input);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="d6bf8-173">Load(XPathNavigator input, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="d6bf8-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="d6bf8-175">Load(IXPathNavigable stylesheet);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="d6bf8-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="d6bf8-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence); </span><span class="sxs-lookup"><span data-stu-id="d6bf8-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
|<span data-ttu-id="d6bf8-178">Load(XmlReader stylesheet);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="d6bf8-179">Load(XmlReader stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="d6bf8-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|  
  
 <span data-ttu-id="d6bf8-181">In der folgenden Tabelle werden die veralteten und die neuen Methoden für die <xref:System.Xml.Xsl.XslTransform.Transform%2A>-Methode aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="d6bf8-182">Die neuen Methoden akzeptieren ein <xref:System.Xml.XmlResolver>-Objekt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
|<span data-ttu-id="d6bf8-183">Veraltete Transform-Methoden in .NET Framework Version 1.0</span><span class="sxs-lookup"><span data-stu-id="d6bf8-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="d6bf8-184">Ersatz .NET Framework, Version 1.1-Transform-Methoden</span><span class="sxs-lookup"><span data-stu-id="d6bf8-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|  
|-----------------------------------------------------------|--------------------------------------------------------------|  
|<span data-ttu-id="d6bf8-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="d6bf8-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="d6bf8-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="d6bf8-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="d6bf8-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="d6bf8-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="d6bf8-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="d6bf8-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="d6bf8-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="d6bf8-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|  
|<span data-ttu-id="d6bf8-201">Void Transform(String input, String output);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="d6bf8-202">Void Transform(String input, String output, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="d6bf8-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|  
  
 <span data-ttu-id="d6bf8-203">Die <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType>-Eigenschaft ist in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], Version 1.1, veraltet.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.1.</span></span> <span data-ttu-id="d6bf8-204">Verwenden Sie stattdessen die neuen <xref:System.Xml.Xsl.XslTransform.Transform%2A> welche Überladungen ein <xref:System.Xml.XmlResolver> Objekt.</span><span class="sxs-lookup"><span data-stu-id="d6bf8-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6bf8-205">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d6bf8-205">See Also</span></span>  
 <xref:System.Xml.Xsl.XslTransform>  
 [<span data-ttu-id="d6bf8-206">XSLT-Transformationen mit der XslTransform-Klasse</span><span class="sxs-lookup"><span data-stu-id="d6bf8-206">XSLT Transformations with the XslTransform Class</span></span>](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [<span data-ttu-id="d6bf8-207">"XPathNavigator" in Transformationen</span><span class="sxs-lookup"><span data-stu-id="d6bf8-207">XPathNavigator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [<span data-ttu-id="d6bf8-208">"XPathNodeIterator" in Transformationen</span><span class="sxs-lookup"><span data-stu-id="d6bf8-208">XPathNodeIterator in Transformations</span></span>](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [<span data-ttu-id="d6bf8-209">XPathDocument-Eingaben in "XslTransform"</span><span class="sxs-lookup"><span data-stu-id="d6bf8-209">XPathDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [<span data-ttu-id="d6bf8-210">XmlDataDocument-Eingaben in "XslTransform"</span><span class="sxs-lookup"><span data-stu-id="d6bf8-210">XmlDataDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [<span data-ttu-id="d6bf8-211">XmlDocument-Eingaben in "XslTransform"</span><span class="sxs-lookup"><span data-stu-id="d6bf8-211">XmlDocument Input to XslTransform</span></span>](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)