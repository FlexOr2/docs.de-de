---
title: 'Schleifen: while...do-Ausdruck (F#)'
description: Finden Sie unter wie beim... führen Ausdruck wird verwendet, um iterative Ausführung (Schleifen) auszuführen, während eine bestimmte testbedingung erfüllt ist.
ms.date: 05/16/2016
ms.openlocfilehash: 5cf4461669221f91cb50e238c25494f03a10bbc2
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "45664708"
---
# <a name="loops-whiledo-expression"></a>Schleifen: while...do-Ausdruck

Die `while...do` Ausdruck wird verwendet, um iterative Ausführung (Schleifen) auszuführen, während eine bestimmte testbedingung erfüllt ist.

## <a name="syntax"></a>Syntax

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Hinweise

Die *Testausdruck* ausgewertet wird, ist dies `true`, *Body-Ausdruck* ausgeführt wird und der Testausdruck erneut ausgewertet wird. Die *Body-Ausdruck* muss einen Typ aufweisen `unit`. Wenn der Testausdruck ist `false`, die Iteration beendet.

Das folgende Beispiel veranschaulicht die Verwendung der `while...do` Ausdruck.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Die Ausgabe des obigen Codes ist es sich um einen Stream von Zufallszahlen zwischen 1 und 20, die, der letzten der 10 ist.

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE]
Können Sie `while...do` in Sequenzausdrücken und anderen Berechnungsausdrücken in diesem Fall, dass eine angepasste Version von der `while...do` Ausdruck wird verwendet. Weitere Informationen finden Sie unter [Sequenzen](sequences.md), [asynchrone Workflows](asynchronous-workflows.md), und [Berechnungsausdrücke](computation-expressions.md).

## <a name="see-also"></a>Siehe auch

- [F#-Sprachreferenz](index.md)
- [Schleifen: `for...in`-Ausdruck](loops-for-in-expression.md)
- [Schleifen: `for...to`-Ausdruck](loops-for-to-expression.md)
