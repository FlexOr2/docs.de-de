---
title: 'Vorgehensweise: Verwenden von Ausdrucksbaumstrukturen zum Erstellen dynamischer Abfragen (C#)'
ms.date: 07/20/2015
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
ms.openlocfilehash: e3afbea647bb429d25f41f37fde268565bc5bf8a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2018
ms.locfileid: "45591411"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Vorgehensweise: Verwenden von Ausdrucksbaumstrukturen zum Erstellen dynamischer Abfragen (C#)
Ausdrucksbaumstrukturen werden in LINQ dazu verwendet, strukturierte Abfragen für Datenquellen zu repräsentieren, die <xref:System.Linq.IQueryable%601> implementieren. Der LINQ-Anbieter implementiert z.B. die <xref:System.Linq.IQueryable%601>-Schnittstelle, um relationale Datenspeicher abzufragen. Die Compiler für C# kompilieren Abfragen solcher Datenquellen in Code, der zur Laufzeit eine Ausdrucksbaumstruktur erzeugt. Anschließend kann der Abfrageanbieter die Datenstruktur der Ausdrucksbaumstruktur durchlaufen und in eine für die Datenquelle geeignete Abfragesprache übersetzen.  
  
 Ausdrucksbaumstrukturen werden in LINQ außerdem dazu verwendet, Lambdaausdrücke zu repräsentieren, die Variablen den Typs <xref:System.Linq.Expressions.Expression%601> zugewiesen sind.  
  
 In diesem Thema wird erläutert, wie Sie Ausdrucksbaumstrukturen verwenden können, um dynamische LINQ-Abfragen zu erstellen. Dynamische Abfragen sind nützlich, wenn die Eigenschaften einer Abfrage zur Kompilierzeit nicht bekannt sind. Beispielsweise kann eine Anwendung über eine Benutzeroberfläche verfügen, in der der Endbenutzer ein oder mehrere Prädikate zum Filtern der Daten angeben kann. Damit LINQ für Abfragen verwendet werden kann, muss solch eine Anwendung Ausdrucksbaumstrukturen benutzen, um die LINQ-Abfrage zur Laufzeit zu erstellen.  
  
## <a name="example"></a>Beispiel  
 In folgendem Beispiel erfahren Sie, wie Sie Ausdrucksbaumstrukturen zur Konstruktion einer Abfrage anhand einer `IQueryable`-Datenquelle verwenden und diese anschließend ausführen können. Im Code wird eine Ausdrucksbaumstruktur erstellt, welche die folgende Abfrage darstellt:  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Die Factorymethoden im <xref:System.Linq.Expressions>-Namespace werden zum Erstellen von Ausdrucksbaumstrukturen verwendet, die Ausdrücke repräsentieren, aus denen die Abfrage besteht. Die Ausdrücke, die Aufrufe an die Methoden des Standardabfrageoperators repräsentieren, verweisen auf die <xref:System.Linq.Queryable>-Implementierung dieser Methoden. Die letzte Verzeichnisstruktur wird an die <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>-Implementierung des Anbieters der `IQueryable`-Datenquelle übergeben, um eine ausführbare Abfrage des Typs `IQueryable` zu erstellen. Sie erhalten die Ergebnisse via Zugriff auf die Auflistung der Abfrageergebnisse.  
  
```csharp  
// Add a using directive for System.Linq.Expressions.  
  
string[] companies = { "Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",  
                   "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",  
                   "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",  
                   "Blue Yonder Airlines", "Trey Research", "The Phone Company",  
                   "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee" };  
  
// The IQueryable data to query.  
IQueryable<String> queryableData = companies.AsQueryable<string>();  
  
// Compose the expression tree that represents the parameter to the predicate.  
ParameterExpression pe = Expression.Parameter(typeof(string), "company");  
  
// ***** Where(company => (company.ToLower() == "coho winery" || company.Length > 16)) *****  
// Create an expression tree that represents the expression 'company.ToLower() == "coho winery"'.  
Expression left = Expression.Call(pe, typeof(string).GetMethod("ToLower", System.Type.EmptyTypes));  
Expression right = Expression.Constant("coho winery");  
Expression e1 = Expression.Equal(left, right);  
  
// Create an expression tree that represents the expression 'company.Length > 16'.  
left = Expression.Property(pe, typeof(string).GetProperty("Length"));  
right = Expression.Constant(16, typeof(int));  
Expression e2 = Expression.GreaterThan(left, right);  
  
// Combine the expression trees to create an expression tree that represents the  
// expression '(company.ToLower() == "coho winery" || company.Length > 16)'.  
Expression predicateBody = Expression.OrElse(e1, e2);  
  
// Create an expression tree that represents the expression  
// 'queryableData.Where(company => (company.ToLower() == "coho winery" || company.Length > 16))'  
MethodCallExpression whereCallExpression = Expression.Call(  
    typeof(Queryable),  
    "Where",  
    new Type[] { queryableData.ElementType },  
    queryableData.Expression,  
    Expression.Lambda<Func<string, bool>>(predicateBody, new ParameterExpression[] { pe }));  
// ***** End Where *****  
  
// ***** OrderBy(company => company) *****  
// Create an expression tree that represents the expression  
// 'whereCallExpression.OrderBy(company => company)'  
MethodCallExpression orderByCallExpression = Expression.Call(  
    typeof(Queryable),  
    "OrderBy",  
    new Type[] { queryableData.ElementType, queryableData.ElementType },  
    whereCallExpression,  
    Expression.Lambda<Func<string, string>>(pe, new ParameterExpression[] { pe }));  
// ***** End OrderBy *****  
  
// Create an executable query from the expression tree.  
IQueryable<string> results = queryableData.Provider.CreateQuery<string>(orderByCallExpression);  
  
// Enumerate the results.  
foreach (string company in results)  
    Console.WriteLine(company);  
  
/*  This code produces the following output:  
  
    Blue Yonder Airlines  
    City Power & Light  
    Coho Winery  
    Consolidated Messenger  
    Graphic Design Institute  
    Humongous Insurance  
    Lucerne Publishing  
    Northwind Traders  
    The Phone Company  
    Wide World Importers  
*/  
```  
  
 In diesem Code wird in dem an die `Queryable.Where`-Methode übergebenen Prädikat eine feste Anzahl von Ausdrücken verwendet. Sie können allerdings eine Anwendung schreiben, die eine variable Zahl von Prädikatausdrücken miteinander vereint; diese Zahl ist von der Benutzereingabe abhängig. Sie können auch die Standardabfrageoperatoren variieren, die in der Abfrage aufgerufen werden; dies ist ebenfalls von der Benutzereingabe abhängig.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
  
-   Erstellen Sie ein neues **Konsolenanwendungsprojekt**.  
  
-   Fügen Sie einen Verweis auf „System.Core.dll“ hinzu, wenn nicht bereits darauf verwiesen wird.  
  
-   Binden Sie den System.Linq.Expressions-Namespace ein.  
  
-   Kopieren Sie den Code aus dem ersten Beispiel, und fügen Sie ihn in die `Main`-Methode ein.  
  
## <a name="see-also"></a>Siehe auch

- [Ausdrucksbaumstrukturen (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [Vorgehensweise: Ausführen von Ausdrucksbaumstrukturen (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
- [Gewusst wie: Dynamisches Festlegen von Prädikatfiltern zur Laufzeit](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
