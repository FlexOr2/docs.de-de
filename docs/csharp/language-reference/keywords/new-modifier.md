---
title: new-Modifizierer (C#-Referenz)
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 496339a7c3b95f16fd13479b096d90058b0799d4
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2018
ms.locfileid: "46702672"
---
# <a name="new-modifier-c-reference"></a>new-Modifizierer (C#-Referenz)

Wenn das Schlüsselwort `new` als Deklarationsmodifizierer verwendet wird, blendet es explizit einen von einer Basisklasse geerbten Member aus. Wenn Sie einen geerbten Member ausblenden, ersetzt die abgeleitete Version des Members die Basisklassenversion. Obwohl Sie Member verdecken können, ohne den `new`-Modifizierer zu verwenden, wird eine Compilerwarnung angezeigt. Wenn Sie `new` verwenden, um einen Member explizit auszublenden, wird diese Warnung unterdrückt.

Um einen geerbten Member auszublenden, deklarieren Sie ihn mit demselben Membernamen in der abgeleiteten Klasse und ändern ihn mit dem `new`-Schlüsselwort. Zum Beispiel:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

In diesem Beispiel wird `BaseC.Invoke` durch `DerivedC.Invoke` ausgeblendet. Der Vorgang wirkt sich nicht auf das Feld `x` aus, da es nicht mit einem ähnlichen Namen ausgeblendet wird.

Das Ausblenden des Namens durch Vererbung nimmt eine der folgenden Formen an:

Im Allgemeinen blendet eine Konstante, ein Feld, eine Eigenschaft oder einen Typ, der in einer Klasse oder Struktur eingegeben wird, alle Basisklassenmember aus, die den gleichen Namen haben.  Es werden bestimmte Fälle unterschieden.  Wenn Sie beispielsweise ein neues Feld mit dem Namen `N` mit einem nicht aufrufbaren Typ deklarieren, und ein Basistyp deklariert `N` als Methode, blendet das neue Feld die Basisdeklaration nicht in der Aufrufsyntax aus.  Weitere Informationen finden Sie unter [C# 5.0-Sprachspezifikation](https://www.microsoft.com/download/details.aspx?id=7029) (siehe Abschnitt „Suche nach Membern“ im Abschnitt „Ausdrücke“).

Durch eine Methode, die in eine Klasse oder Struktur eingeführt ist, werden Eigenschaften, Felder und Typen mit dem gleichen Namen in der Basisklasse ausgeblendet. Alle Basisklassenmethoden mit der gleichen Signatur werden ebenfalls ausgeblendet.

Durch einen Indexer, der in einer Klasse oder Struktur eingeführt ist, werden alle Basisklassenindexer mit der gleichen Signatur ausgeblendet.

`new` und [override](override.md) dürfen nicht gleichzeitig auf denselben Member angewendet werden, da sich die Bedeutungen der beiden Modifizierer gegenseitig ausschließen. Mit dem `new`-Modifizierer wird ein neuer Member mit demselben Namen erstellt, und der ursprüngliche Member wird ausgeblendet. Der `override`-Modifizierer verlängert die Implementierung für einen geerbten Member.

Wenn der `new`-Modifizierer in einer Deklaration verwendet wird, in der kein geerbter Member ausgeblendet wird, wird eine Warnung generiert.

## <a name="example"></a>Beispiel

In diesem Beispiel wird von einer Basisklasse, `BaseC`, und einer abgeleiteten Klasse, `DerivedC`, der gleiche Feldname `x` verwendet. Auf diese Weise wird der Wert des geerbten Felds ausgeblendet. Im Beispiel wird die Verwendung des `new`-Modifizierers veranschaulicht. Außerdem wird gezeigt, wie mit den voll qualifizierten Namen auf die ausgeblendeten Member der Basisklasse zugegriffen wird.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Beispiel

In diesem Beispiel blendet eine geschachtelte Klasse eine Klasse mit dem gleichen Namen in der Basisklasse aus. Das Beispiel veranschaulicht, wie mit dem `new`-Modifizierer die Warnmeldung vermieden wird und wie mit den voll qualifizierten Namen auf die ausgeblendeten Klassenmember zugegriffen wird.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Wenn der `new`-Modifizierer entfernt wird, kann das Programm dennoch kompiliert und ausgeführt werden. Es wird jedoch folgende Warnung angezeigt:

```
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>C#-Sprachspezifikation

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../../language-reference/index.md)
- [C#-Programmierhandbuch](../../programming-guide/index.md)
- [C#-Schlüsselwörter](index.md)
- [Operatorschlüsselwörter](operator-keywords.md)
- [Modifizierer](modifiers.md)
- [Versionsverwaltung mit den Schlüsselwörtern "override" und "new"](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Wann müssen die Schlüsselwörter "override" und "new" verwendet werden?](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
