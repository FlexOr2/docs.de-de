---
title: Listen (F#)
description: "Informationen Sie zu F#-Listen, eine geordnete, unveränderliche Reihe von Elementen des gleichen Typs."
keywords: Visual F#, F#, funktionale Programmierung
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a1a6075f-064d-4aee-8222-2b59ff16cc12
ms.openlocfilehash: 5802a5a1c48ad05c1765c4c0fa2e8a81a92dee8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="lists"></a><span data-ttu-id="f87ca-104">Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-104">Lists</span></span>

> [!NOTE]
<span data-ttu-id="f87ca-105">Mit dem API-Referenz-Link in diesem Artikel gelangen Sie auf MSDN.</span><span class="sxs-lookup"><span data-stu-id="f87ca-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="f87ca-106">Die docs.microsoft.com-API-Referenz ist nicht abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f87ca-107">Eine Liste in F# stellt eine geordnete, unveränderliche Reihe von Elementen desselben Typs dar.</span><span class="sxs-lookup"><span data-stu-id="f87ca-107">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="f87ca-108">Um grundlegende Operationen mit Listen durchzuführen, verwenden Sie die Funktionen in der [listenmodul](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="f87ca-108">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>


## <a name="creating-and-initializing-lists"></a><span data-ttu-id="f87ca-109">Erstellen und Initialisieren von Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-109">Creating and Initializing Lists</span></span>
<span data-ttu-id="f87ca-110">Sie können eine Liste definieren, indem Sie die durch Semikolon getrennten und in eckige Klammern eingeschlossenen Elemente explizit auflisten, wie in folgender Codezeile veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f87ca-110">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="f87ca-111">Sie können Elemente auch durch Zeilenumbrüche trennen, wobei die Semikolons dann optional sind.</span><span class="sxs-lookup"><span data-stu-id="f87ca-111">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="f87ca-112">Letztere Syntax kann den Code übersichtlicher gestalten, wenn die Ausdrücke zur Elementinitialisierung umfangreicher ausfallen oder Sie für jedes Element einen Kommentar einbeziehen möchten.</span><span class="sxs-lookup"><span data-stu-id="f87ca-112">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="f87ca-113">Im Allgemeinen müssen alle Listenelemente denselben Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-113">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="f87ca-114">Eine Ausnahme ist, dass eine Liste, in der für Elemente ein Basistyp angegeben wird, Elemente enthalten darf, die abgeleiteten Typen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-114">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="f87ca-115">Somit ist Folgendes zulässig, da sowohl `Button` und `CheckBox` von `Control` abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="f87ca-115">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="f87ca-116">Sie können Listenelemente auch durch Verwendung eines Bereichs definieren, der durch ganze Zahlen angegeben wird, die durch den Bereichsoperator (`..`) getrennt sind, wie im folgenden Code veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f87ca-116">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="f87ca-117">Eine leere Liste wird durch ein Paar eckige Klammern angegeben, die nichts einschließen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-117">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="f87ca-118">Sie können eine Liste auch mithilfe von Sequenzausdrücken erstellen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-118">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="f87ca-119">Finden Sie unter [Sequenzausdrücke](sequences.md#sequence-expressions) für Weitere Informationen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-119">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="f87ca-120">Der folgende Code erstellt z. B. eine Liste mit den Quadratzahlen der ganzen Zahlen von 1 bis 10.</span><span class="sxs-lookup"><span data-stu-id="f87ca-120">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="f87ca-121">Operatoren für die Arbeit mit Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-121">Operators for Working with Lists</span></span>
<span data-ttu-id="f87ca-122">Sie können Elemente mithilfe des Operators `::` (Cons) zu einer Liste hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-122">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="f87ca-123">Wenn `list1` den Werten `[2; 3; 4]` entspricht, erstellt der folgende Code für `list2` die Werte `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-123">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="f87ca-124">Sie können Listen, die kompatible Typen aufweisen, wie im folgenden Code mithilfe des Operators `@` verketten.</span><span class="sxs-lookup"><span data-stu-id="f87ca-124">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="f87ca-125">Wenn `list1` den Werten `[2; 3; 4]` und `list2` den Werten `[100; 2; 3; 4 ]` entspricht, erstellt dieser Code für `list3` die Werte `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-125">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4 ]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="f87ca-126">Es stehen Funktionen zum Ausführen von Operationen mit Listen in die [listenmodul](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="f87ca-126">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="f87ca-127">Da Listen in F# unveränderlich sind, erstellen alle modifizierenden Operationen neue Listen, anstatt die vorhandenen Listen zu verändern.</span><span class="sxs-lookup"><span data-stu-id="f87ca-127">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="f87ca-128">Listen in f# als einfach verknüpfte Listen, was bedeutet, dass Vorgänge, die den Anfang der Liste zugreifen, O(1) entsprechen, implementiert und Elementzugriff ist O (*n*).</span><span class="sxs-lookup"><span data-stu-id="f87ca-128">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>


## <a name="properties"></a><span data-ttu-id="f87ca-129">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="f87ca-129">Properties</span></span>
<span data-ttu-id="f87ca-130">Der Listentyp unterstützt die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="f87ca-130">The list type supports the following properties:</span></span>

|<span data-ttu-id="f87ca-131">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="f87ca-131">Property</span></span>|<span data-ttu-id="f87ca-132">Typ</span><span class="sxs-lookup"><span data-stu-id="f87ca-132">Type</span></span>|<span data-ttu-id="f87ca-133">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f87ca-133">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="f87ca-134">Head</span><span class="sxs-lookup"><span data-stu-id="f87ca-134">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="f87ca-135">Das erste Element.</span><span class="sxs-lookup"><span data-stu-id="f87ca-135">The first element.</span></span>|
|[<span data-ttu-id="f87ca-136">Leere</span><span class="sxs-lookup"><span data-stu-id="f87ca-136">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="f87ca-137">Eine statische Eigenschaft, die eine leere Liste des entsprechenden Typs zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-137">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="f87ca-138">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="f87ca-138">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="f87ca-139">Ergibt `true`, wenn die Liste keine Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="f87ca-139">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="f87ca-140">Item</span><span class="sxs-lookup"><span data-stu-id="f87ca-140">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="f87ca-141">Das Element am angegebenen (nullbasierten) Index.</span><span class="sxs-lookup"><span data-stu-id="f87ca-141">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="f87ca-142">Länge</span><span class="sxs-lookup"><span data-stu-id="f87ca-142">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="f87ca-143">Die Anzahl der Elemente.</span><span class="sxs-lookup"><span data-stu-id="f87ca-143">The number of elements.</span></span>|
|[<span data-ttu-id="f87ca-144">Ende</span><span class="sxs-lookup"><span data-stu-id="f87ca-144">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="f87ca-145">Die Liste ohne das erste Element.</span><span class="sxs-lookup"><span data-stu-id="f87ca-145">The list without the first element.</span></span>|
<span data-ttu-id="f87ca-146">Nachfolgend sind einige Beispiele zur Verwendung dieser Eigenschaften aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-146">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a><span data-ttu-id="f87ca-147">Verwenden von Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-147">Using Lists</span></span>
<span data-ttu-id="f87ca-148">Durch die Programmierung mit Listen können Sie mit wenig Code komplexe Operationen durchführen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-148">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="f87ca-149">In diesem Abschnitt werden die allgemeinen Operationen für Listen beschrieben, die für die funktionale Programmierung von Bedeutung sind.</span><span class="sxs-lookup"><span data-stu-id="f87ca-149">This section describes common operations on lists that are important to functional programming.</span></span>


### <a name="recursion-with-lists"></a><span data-ttu-id="f87ca-150">Rekursion mit Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-150">Recursion with Lists</span></span>
<span data-ttu-id="f87ca-151">Listen sind beispiellos für rekursive Programmierverfahren geeignet.</span><span class="sxs-lookup"><span data-stu-id="f87ca-151">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="f87ca-152">Betrachten Sie eine Operation, die für jedes Element einer Liste ausgeführt werden muss.</span><span class="sxs-lookup"><span data-stu-id="f87ca-152">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="f87ca-153">Sie können dazu rekursiv vorgehen, indem Sie den Listenanfang verarbeiten und dann den Rest der Liste, bei dem es sich um eine kleinere Liste handelt, die aus der ursprünglichen Liste ohne das erste Element besteht, zurück an die nächste Rekursionsstufe übergeben.</span><span class="sxs-lookup"><span data-stu-id="f87ca-153">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="f87ca-154">Sie verwenden zum Schreiben einer derartigen rekursiven Funktion den Cons-Operator (`::`) für den Mustervergleich, der es Ihnen ermöglicht, den Listenanfang vom Rest zu trennen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-154">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="f87ca-155">Das folgende Codebeispiel zeigt, wie eine rekursive Funktion mithilfe des Mustervergleichs implementiert wird, die Operationen mit einer Liste ausführt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-155">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="f87ca-156">Der vorherige Code ist für kleine Listen geeignet, aber bei größeren Listen könnten Stapelüberläufe auftreten.</span><span class="sxs-lookup"><span data-stu-id="f87ca-156">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="f87ca-157">Der folgende Code verwendet ein Akkumulatorargument, ein Standardverfahren für die Arbeit mit rekursiven Funktionen, um den vorherigen Code zu verbessern.</span><span class="sxs-lookup"><span data-stu-id="f87ca-157">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="f87ca-158">Durch die Verwendung des Akkumulatorarguments wird die Funktion zur endrekursiven Funktion, wodurch Stapelspeicher gespart wird.</span><span class="sxs-lookup"><span data-stu-id="f87ca-158">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="f87ca-159">Die Funktion `RemoveAllMultiples` ist eine rekursive Funktion, die zwei Listen übernimmt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-159">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="f87ca-160">Die erste Liste enthält die Zahlen, deren Vielfaches entfernt wird. Die zweite Liste ist die Liste, aus der die Zahlen entfernt werden.</span><span class="sxs-lookup"><span data-stu-id="f87ca-160">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="f87ca-161">Der Code im folgenden Beispiel verwendet diese rekursive Funktion, um alle Nicht-Primzahlen aus der Liste zu entfernen, sodass als Ergebnis eine Liste der Primzahlen verbleibt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-161">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="f87ca-162">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-162">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="f87ca-163">Modulfunktionen</span><span class="sxs-lookup"><span data-stu-id="f87ca-163">Module Functions</span></span>
<span data-ttu-id="f87ca-164">Die [List-Modul](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) bietet Funktionen, die die Elemente einer Liste zugreifen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-164">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="f87ca-165">Auf das Anfangselement kann am schnellsten und einfachsten zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="f87ca-165">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="f87ca-166">Verwenden Sie die Eigenschaft [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) oder der Modulfunktion [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="f87ca-166">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="f87ca-167">Sie erreichen das Ende einer Liste mit den [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) Eigenschaft oder die [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) Funktion.</span><span class="sxs-lookup"><span data-stu-id="f87ca-167">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="f87ca-168">Um ein Element über einen Index zu suchen, verwenden die [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) Funktion.</span><span class="sxs-lookup"><span data-stu-id="f87ca-168">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="f87ca-169">Mithilfe von `List.nth` wird die Liste durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-169">`List.nth` traverses the list.</span></span> <span data-ttu-id="f87ca-170">Daher ist es O (*n*).</span><span class="sxs-lookup"><span data-stu-id="f87ca-170">Therefore, it is O(*n*).</span></span> <span data-ttu-id="f87ca-171">Wenn in Ihrem Code häufig `List.nth` verwendet wird, können Sie erwägen, ob Sie anstelle der Liste ein Array verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="f87ca-171">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="f87ca-172">Der Elementzugriff in Arrays entspricht "O(1)".</span><span class="sxs-lookup"><span data-stu-id="f87ca-172">Element access in arrays is O(1).</span></span>


### <a name="boolean-operations-on-lists"></a><span data-ttu-id="f87ca-173">Boolesche Operationen für Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-173">Boolean Operations on Lists</span></span>
<span data-ttu-id="f87ca-174">Die [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) -Funktion bestimmt, ob eine Liste Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="f87ca-174">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="f87ca-175">Die [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) -Funktion wendet einen booleschen Test auf Elemente einer Liste und gibt `true` , wenn ein Element den Test erfüllt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-175">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="f87ca-176">[List. exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) ist ähnlich, aber aufeinander folgenden Elementpaare in zwei Listen arbeitet.</span><span class="sxs-lookup"><span data-stu-id="f87ca-176">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="f87ca-177">Das folgende Codebeispiel veranschaulicht die Verwendung von `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-177">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="f87ca-178">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-178">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="f87ca-179">Das folgende Beispiel veranschaulicht die Verwendung von `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-179">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="f87ca-180">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-180">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="f87ca-181">Sie können [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) sollten Sie überprüfen, ob alle Elemente einer Liste eine Bedingung erfüllen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-181">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="f87ca-182">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-182">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="f87ca-183">Auf ähnliche Weise [List. forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) bestimmt, ob alle Elemente in den entsprechenden Positionen in zwei Listen einen booleschen Ausdruck erfüllen, die jedes Elementpaar einbezieht.</span><span class="sxs-lookup"><span data-stu-id="f87ca-183">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="f87ca-184">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-184">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="f87ca-185">Sortieroperationen für Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-185">Sort Operations on Lists</span></span>
<span data-ttu-id="f87ca-186">Die [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), und [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) Funktionen sortieren Listen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-186">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="f87ca-187">Die Sortierfunktion bestimmt, welche dieser drei Funktionen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f87ca-187">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="f87ca-188">`List.sort` verwendet einen generischen Standardvergleich.</span><span class="sxs-lookup"><span data-stu-id="f87ca-188">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="f87ca-189">Beim generischen Vergleich werden globale Operatoren, die auf der allgemeinen Vergleichsfunktion basieren, zum Vergleichen von Werten verwendet.</span><span class="sxs-lookup"><span data-stu-id="f87ca-189">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="f87ca-190">Der generische Vergleich funktioniert mit einer Vielzahl von Elementtypen sehr effizient, z. B. mit einfachen numerischen Typen, Tupeln, Datensätzen, diskriminierten Unions, Listen, Arrays und allen anderen Typen, die `System.IComparable` implementieren.</span><span class="sxs-lookup"><span data-stu-id="f87ca-190">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="f87ca-191">Für Typen, die `System.IComparable` implementieren, wird für den generischen Vergleich die Funktion `System.IComparable.CompareTo()` verwendet.</span><span class="sxs-lookup"><span data-stu-id="f87ca-191">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="f87ca-192">Der generische Vergleich funktioniert auch mit Zeichenfolgen, wobei jedoch eine kulturunabhängige Sortierreihenfolge verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f87ca-192">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="f87ca-193">Der generische Vergleich sollte nicht für Typen verwendet werden, die nicht unterstützt werden, z. B. für Funktionstypen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-193">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="f87ca-194">Die optimale Leistung erzielt der generische Standardvergleich außerdem für kleine strukturierte Typen. Für größere strukturierte Typen, die häufig verglichen und sortiert werden müssen, sollten Sie die Implementierung von `System.IComparable` erwägen und eine effiziente Implementierung der Methode `System.IComparable.CompareTo()` bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-194">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="f87ca-195">`List.sortBy` übernimmt eine Funktion, die einen Wert zurückgibt, der als Sortierkriterium verwendet wird, während `List.sortWith` eine Vergleichsfunktion als Argument übernimmt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-195">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="f87ca-196">Die letzten beiden Funktionen sind hilfreich, wenn Sie mit Typen arbeiten, die keinen Vergleich unterstützen bzw. wenn der Vergleich eine komplexere Vergleichssemantik als bei kulturfähige Zeichenfolgen erfordert.</span><span class="sxs-lookup"><span data-stu-id="f87ca-196">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="f87ca-197">Das folgende Beispiel veranschaulicht die Verwendung von `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-197">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="f87ca-198">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-198">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="f87ca-199">Das folgende Beispiel veranschaulicht die Verwendung von `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-199">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="f87ca-200">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-200">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="f87ca-201">Das nächste Beispiel veranschaulicht die Verwendung von `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-201">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="f87ca-202">In diesem Beispiel wird die benutzerdefinierte Vergleichsfunktion `compareWidgets` zunächst dazu verwendet, um ein Feld mit benutzerdefiniertem Typ zu vergleichen. Anschließend wird ein weiteres Feld verglichen, wenn die Werte des ersten Felds gleich sind.</span><span class="sxs-lookup"><span data-stu-id="f87ca-202">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="f87ca-203">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-203">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="f87ca-204">Suchoperationen für Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-204">Search Operations on Lists</span></span>
<span data-ttu-id="f87ca-205">Für Listen werden zahlreiche Suchoperationen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-205">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="f87ca-206">Die einfachste [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), können Sie das erste Element finden, die einer bestimmten Bedingung übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-206">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="f87ca-207">Das folgende Codebeispiel veranschaulicht die Verwendung von `List.find` anhand der Suche nach der ersten Zahl in einer Liste, die durch fünf geteilt werden kann.</span><span class="sxs-lookup"><span data-stu-id="f87ca-207">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="f87ca-208">The result is 5.</span><span class="sxs-lookup"><span data-stu-id="f87ca-208">The result is 5.</span></span>

<span data-ttu-id="f87ca-209">Wenn die Elemente zunächst transformiert werden müssen, rufen Sie [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), das einer Funktion übernimmt eine Option zurückgibt und sucht nach dem ersten Wert ist `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-209">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="f87ca-210">Anstatt ein Element zurückzugeben, gibt `List.pick` das Ergebnis `x` zurück.</span><span class="sxs-lookup"><span data-stu-id="f87ca-210">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="f87ca-211">Wenn kein übereinstimmendes Element gefunden wird, löst `List.pick` die Ausnahme `System.Collections.Generic.KeyNotFoundException` aus.</span><span class="sxs-lookup"><span data-stu-id="f87ca-211">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="f87ca-212">Im folgenden Code wird die Verwendung von `List.pick` veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="f87ca-212">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="f87ca-213">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-213">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="f87ca-214">Eine andere Gruppe von Suchoperationen, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) und verwandte Funktionen geben einen Optionswert zurück.</span><span class="sxs-lookup"><span data-stu-id="f87ca-214">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="f87ca-215">Die `List.tryFind`-Funktion gibt das erste Element einer Liste zurück, das eine Bedingung erfüllt, sofern dieses Element vorhanden ist. Wenn dies nicht der Fall ist, wird der Optionswert `None` zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="f87ca-215">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="f87ca-216">Die Variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) gibt den Index des Elements zurück, wenn eines, anstatt das Element selbst gefunden wird.</span><span class="sxs-lookup"><span data-stu-id="f87ca-216">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="f87ca-217">Diese Funktionen werden im folgenden Code veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f87ca-217">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="f87ca-218">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-218">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="f87ca-219">Arithmetische Operationen für Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-219">Arithmetic Operations on Lists</span></span>
<span data-ttu-id="f87ca-220">Allgemeine arithmetische Operationen wie Summe und Mittelwert sind in integriert die [listenmodul](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="f87ca-220">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="f87ca-221">Zur Bearbeitung [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), muss der Listenelementtyp unterstützen die `+` Operator und einen Nullwert besitzen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-221">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="f87ca-222">Alle integrierten arithmetischen Typen erfüllen diese Bedingungen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-222">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="f87ca-223">Zur Bearbeitung [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), der Elementtyp Division ohne Rest, die ganzzahlige Typen ausgeschlossen, aber Gleitkommatypen ermöglicht unterstützen muss.</span><span class="sxs-lookup"><span data-stu-id="f87ca-223">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="f87ca-224">Die [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) und [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) Funktionen nehmen eine Funktion als Parameter, und die Ergebnisse dieser Funktion werden verwendet, um die Werte für die Summe oder den Mittelwert zu berechnen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-224">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="f87ca-225">Das folgende Codebeispiel veranschaulicht die Verwendung von `List.sum`, `List.sumBy` und `List.average`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-225">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="f87ca-226">Die Ausgabe lautet `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-226">The output is `1.000000`.</span></span>

<span data-ttu-id="f87ca-227">Im folgenden Code wird die Verwendung von `List.averageBy` veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="f87ca-227">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="f87ca-228">Die Ausgabe lautet `5.5`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-228">The output is `5.5`.</span></span>


### <a name="lists-and-tuples"></a><span data-ttu-id="f87ca-229">Listen und Tupel</span><span class="sxs-lookup"><span data-stu-id="f87ca-229">Lists and Tuples</span></span>
<span data-ttu-id="f87ca-230">Listen, die Tupel enthalten, können mithilfe von Funktionen zum Zippen und Entzippen verändert werden.</span><span class="sxs-lookup"><span data-stu-id="f87ca-230">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="f87ca-231">Diese Funktionen vereinen zwei Listen mit einzelnen Werten zu einer Liste von Tupeln oder unterteilen eine Liste von Tupeln in zwei Listen mit einzelnen Werten.</span><span class="sxs-lookup"><span data-stu-id="f87ca-231">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="f87ca-232">Die einfachste [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) -Funktion übernimmt zwei Listen mit einzelnen Elementen und erzeugt eine einzelne Liste von Tupelpaaren.</span><span class="sxs-lookup"><span data-stu-id="f87ca-232">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="f87ca-233">Eine andere Version [List. zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), übernimmt drei Listen mit einzelnen Elementen und erzeugt eine einzelne Liste von Tupeln, die drei Elemente umfassen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-233">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="f87ca-234">Das folgende Codebeispiel veranschaulicht die Verwendung von `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-234">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="f87ca-235">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-235">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="f87ca-236">Das folgende Codebeispiel veranschaulicht die Verwendung von `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-236">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="f87ca-237">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-237">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="f87ca-238">Die entsprechenden Versionen zum Entzippen, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) und [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), übernehmen Listen mit Tupeln und Listen in einem Tupel zurück, in denen enthält der ersten Liste alle Elemente, die zuerst in jedem Tupel, und die zweite Liste enthält das zweite Element jedes Tupels und So weiter.</span><span class="sxs-lookup"><span data-stu-id="f87ca-238">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="f87ca-239">Das folgende Codebeispiel veranschaulicht die Verwendung von [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="f87ca-239">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="f87ca-240">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-240">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="f87ca-241">Das folgende Codebeispiel veranschaulicht die Verwendung von [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="f87ca-241">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="f87ca-242">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-242">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="f87ca-243">Arbeiten mit Listenelementen</span><span class="sxs-lookup"><span data-stu-id="f87ca-243">Operating on List Elements</span></span>
<span data-ttu-id="f87ca-244">F# unterstützt eine Vielzahl von Operationen mit Listenelementen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-244">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="f87ca-245">Die einfachste Technologie ist [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), können Sie eine Funktion auf jedes Element einer Liste aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-245">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="f87ca-246">Variationen [List. iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), können Sie einen Vorgang auf die Elemente zweier Listen ausführen [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), also z. B. `List.iter` mit dem Unterschied, dass der Index der einzelnen Elemente als übergeben wird ein Argument für die Funktion, die für jedes Element aufgerufen wird und [List. iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), dies ist eine Kombination der Funktionen der `List.iter2` und `List.iteri`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-246">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="f87ca-247">Diese Funktionen werden im folgenden Codebeispiel veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="f87ca-247">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="f87ca-248">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-248">The output is as follows:</span></span>

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="f87ca-249">Eine andere häufig verwendete Funktion, die von Listenelementen ist [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), sodass Sie eine Funktion auf jedes Element einer Liste anwenden und alle Ergebnisse in eine neue Liste.</span><span class="sxs-lookup"><span data-stu-id="f87ca-249">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="f87ca-250">[List. map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) und [List. map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) sind Variationen, die mehrere Listen übernehmen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-250">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="f87ca-251">Sie können auch [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) und [List. mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), wenn die Funktion zusätzlich zum Element, muss der Index der einzelnen Elemente übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="f87ca-251">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="f87ca-252">Der einzige Unterschied zwischen `List.mapi2` und `List.mapi` besteht darin, dass `List.mapi2` mit zwei Listen arbeitet.</span><span class="sxs-lookup"><span data-stu-id="f87ca-252">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="f87ca-253">Das folgende Beispiel veranschaulicht [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="f87ca-253">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="f87ca-254">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-254">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="f87ca-255">Im folgenden Beispiel wird eine Verwendung von `List.map2` gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-255">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="f87ca-256">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-256">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="f87ca-257">Im folgenden Beispiel wird eine Verwendung von `List.map3` gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-257">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="f87ca-258">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-258">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="f87ca-259">Im folgenden Beispiel wird eine Verwendung von `List.mapi` gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-259">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="f87ca-260">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-260">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="f87ca-261">Im folgenden Beispiel wird eine Verwendung von `List.mapi2` gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-261">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="f87ca-262">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-262">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="f87ca-263">[List.Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) entspricht `List.map`, außer, dass jedes Element eine Liste erzeugt und sämtliche Listen zu einer abschließenden Liste verkettet werden.</span><span class="sxs-lookup"><span data-stu-id="f87ca-263">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="f87ca-264">Im folgenden Code generiert jedes Element der Liste drei Zahlen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-264">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="f87ca-265">Diese werden alle in einer Liste erfasst.</span><span class="sxs-lookup"><span data-stu-id="f87ca-265">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="f87ca-266">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-266">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="f87ca-267">Sie können auch [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), die eine booleschen Bedingung übernimmt und erzeugt eine neue Liste, die nur von Elementen besteht, die die angegebene Bedingung erfüllen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-267">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="f87ca-268">Die Ergebnisliste lautet `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-268">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="f87ca-269">Eine Kombination aus Zuordnung und Filter [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) ermöglicht es Ihnen, Transformieren und Auswählen von Elementen zur gleichen Zeit.</span><span class="sxs-lookup"><span data-stu-id="f87ca-269">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="f87ca-270">`List.choose` wendet eine Funktion an, die eine Option zu den einzelnen Elementen einer Liste zurückgibt, und gibt eine neue Liste der Ergebnisse für Elemente zurück, wenn die Funktion den Optionswert `Some` liefert.</span><span class="sxs-lookup"><span data-stu-id="f87ca-270">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="f87ca-271">Der folgende Code veranschaulicht die Verwendung von `List.choose`, um Wörter in Großbuchstaben aus einer Wörterliste auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-271">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="f87ca-272">Die Ausgabe lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="f87ca-272">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="f87ca-273">Arbeiten mit mehreren Listen</span><span class="sxs-lookup"><span data-stu-id="f87ca-273">Operating on Multiple Lists</span></span>
<span data-ttu-id="f87ca-274">Listen können verknüpft werden.</span><span class="sxs-lookup"><span data-stu-id="f87ca-274">Lists can be joined together.</span></span> <span data-ttu-id="f87ca-275">Um zwei Listen zu einer zu verknüpfen, verwenden Sie [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="f87ca-275">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="f87ca-276">Um mehr als zwei Listen zu verknüpfen, verwenden Sie [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="f87ca-276">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a><span data-ttu-id="f87ca-277">Falt- und Suchoperationen</span><span class="sxs-lookup"><span data-stu-id="f87ca-277">Fold and Scan Operations</span></span>
<span data-ttu-id="f87ca-278">Einige Listenoperationen umfassen gegenseitige Abhängigkeiten zwischen allen Listenelementen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-278">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="f87ca-279">Die Falt- und Suchoperationen Verhalten sich wie `List.iter` und `List.map` dahingehend, dass Sie für jedes Element eine Funktion aufrufen, aber diese Operationen einen zusätzlichen Parameter namens Stellen der *Akkumulator* enthält, die Informationen über die Berechnung.</span><span class="sxs-lookup"><span data-stu-id="f87ca-279">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="f87ca-280">Verwenden Sie `List.fold`, um eine Berechnung für eine Liste durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-280">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="f87ca-281">Das folgende Codebeispiel veranschaulicht die Verwendung von [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) um verschiedene Operationen durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-281">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="f87ca-282">Die Liste wird durchlaufen. Der Akkumulator `acc` ist ein Wert, der mit voranschreitender Berechnung weitergegeben wird.</span><span class="sxs-lookup"><span data-stu-id="f87ca-282">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="f87ca-283">Das erste Argument übernimmt den Akkumulator sowie das Listenelement und gibt das Zwischenergebnis der Berechnung für dieses Listenelement zurück.</span><span class="sxs-lookup"><span data-stu-id="f87ca-283">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="f87ca-284">Das zweite Argument ist der Ausgangswert des Akkumulators.</span><span class="sxs-lookup"><span data-stu-id="f87ca-284">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="f87ca-285">Die Versionen dieser Funktionen, die eine Ziffer im Funktionsnamen enthalten, arbeiten mit mehreren Listen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-285">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="f87ca-286">Beispielsweise [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) Berechnungen für zwei Listen ausführt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-286">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="f87ca-287">Das folgende Beispiel veranschaulicht die Verwendung von `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-287">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="f87ca-288">`List.fold`und [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) unterscheiden, die sich `List.fold` den endgültigen Wert des zusätzlichen Parameters zurückgibt, aber `List.scan` gibt die Liste der Zwischenwerte (zusammen mit dem Endwert) des zusätzlichen Parameters zurück.</span><span class="sxs-lookup"><span data-stu-id="f87ca-288">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="f87ca-289">Jede dieser Funktionen umfasst eine umkehrvariante, z. B. [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), die sich unterscheidet, in der Reihenfolge, in der die Liste durchlaufen wird und die Reihenfolge der Argumente.</span><span class="sxs-lookup"><span data-stu-id="f87ca-289">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="f87ca-290">Darüber hinaus `List.fold` und `List.foldBack` Variationen, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) und [List. foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), die zwei Listen gleicher Länge dauern.</span><span class="sxs-lookup"><span data-stu-id="f87ca-290">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="f87ca-291">Die Funktion, die für die einzelnen Elemente ausgeführt wird, kann entsprechende Elemente beider Listen verwenden, um Aktionen durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-291">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="f87ca-292">Die Elementtypen beider Listen können wie im folgenden Beispiel unterschiedlich sein, in dem eine Liste Transaktionsbeträge für ein Bankkonto und die andere Liste den Typ der Transaktion enthält: Einzahlung oder Auszahlung.</span><span class="sxs-lookup"><span data-stu-id="f87ca-292">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="f87ca-293">Für eine Berechnung wie bei der Addition weisen `List.fold` und `List.foldBack` denselben Effekt auf, da das Ergebnis nicht von der Reihenfolge des Durchlaufs abhängt.</span><span class="sxs-lookup"><span data-stu-id="f87ca-293">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="f87ca-294">Im folgenden Beispiel wird `List.foldBack` zum Hinzufügen der Elemente zu einer Liste verwendet.</span><span class="sxs-lookup"><span data-stu-id="f87ca-294">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="f87ca-295">Das folgende Beispiel kehrt zum Bankkontobeispiel zurück.</span><span class="sxs-lookup"><span data-stu-id="f87ca-295">The following example returns to the bank account example.</span></span> <span data-ttu-id="f87ca-296">Dieses Mal wird ein neuer Transaktionstyp hinzugefügt: Zinsberechnung.</span><span class="sxs-lookup"><span data-stu-id="f87ca-296">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="f87ca-297">Der Endsaldo hängt jetzt von der Reihenfolge der Transaktionen ab.</span><span class="sxs-lookup"><span data-stu-id="f87ca-297">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="f87ca-298">Die Funktion [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) sich ähnlich wie `List.fold` und `List.scan`, außer dass anstatt einen separaten Akkumulator, `List.reduce` übernimmt eine Funktion, die zwei Argumente des Elementtyps anstelle von nur eine und von diesen Argumenten fungiert als Akkumulator dient, was bedeutet, dass es das Zwischenergebnis der Berechnung speichert.</span><span class="sxs-lookup"><span data-stu-id="f87ca-298">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="f87ca-299">`List.reduce` beginnt mit der Bearbeitung der ersten beiden Listenelemente und verwendet dann das Ergebnis der Operation zusammen mit dem nächsten Element.</span><span class="sxs-lookup"><span data-stu-id="f87ca-299">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="f87ca-300">Da kein separater Akkumulator mit eigenem Typ vorhanden ist, kann `List.reduce` nur anstelle von `List.fold` verwendet werden, wenn Akkumulator und Elementtyp denselben Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="f87ca-300">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="f87ca-301">Das folgende Codebeispiel veranschaulicht die Verwendung von `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="f87ca-301">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="f87ca-302">`List.reduce` löst eine Ausnahme aus, wenn die bereitgestellte Liste keine Elemente enthält.</span><span class="sxs-lookup"><span data-stu-id="f87ca-302">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="f87ca-303">Im folgenden Code erhält der Lambda-Ausdruck die Argumente "2" und "4" und gibt "6" zurück. Der nächste Aufruf erhält die Argumente "6" und "10", daher ist das Ergebnis "16".</span><span class="sxs-lookup"><span data-stu-id="f87ca-303">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="f87ca-304">Konvertieren zwischen Listen und anderen Auflistungstypen</span><span class="sxs-lookup"><span data-stu-id="f87ca-304">Converting Between Lists and Other Collection Types</span></span>
<span data-ttu-id="f87ca-305">Das `List`-Modul stellt Funktionen zum Konvertieren von Sequenzen in Arrays und umgekehrt bereit.</span><span class="sxs-lookup"><span data-stu-id="f87ca-305">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="f87ca-306">Verwenden Sie zum Konvertieren in oder aus einer Sequenz [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) oder [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="f87ca-306">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="f87ca-307">Um in einen oder aus einem Array zu konvertieren, verwenden Sie [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) oder [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="f87ca-307">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>


### <a name="additional-operations"></a><span data-ttu-id="f87ca-308">Weitere Operationen</span><span class="sxs-lookup"><span data-stu-id="f87ca-308">Additional Operations</span></span>
<span data-ttu-id="f87ca-309">Informationen zu zusätzlichen Operationen für Listen, finden Sie im Referenzthema für die Bibliothek [Collections.List-Modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f87ca-309">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>


## <a name="see-also"></a><span data-ttu-id="f87ca-310">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f87ca-310">See Also</span></span>
[<span data-ttu-id="f87ca-311">F#-Sprachreferenz</span><span class="sxs-lookup"><span data-stu-id="f87ca-311">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="f87ca-312">F#-Typen</span><span class="sxs-lookup"><span data-stu-id="f87ca-312">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="f87ca-313">Sequenzen</span><span class="sxs-lookup"><span data-stu-id="f87ca-313">Sequences</span></span>](sequences.md)

[<span data-ttu-id="f87ca-314">Arrays</span><span class="sxs-lookup"><span data-stu-id="f87ca-314">Arrays</span></span>](arrays.md)

[<span data-ttu-id="f87ca-315">Optionen</span><span class="sxs-lookup"><span data-stu-id="f87ca-315">Options</span></span>](options.md)