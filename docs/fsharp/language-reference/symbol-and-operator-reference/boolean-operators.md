---
title: Boolesche Operatoren (F#)
description: Erfahren Sie, bis die booleschen Operatoren, die in der Programmiersprache F# verfügbar sind.
ms.date: 05/16/2016
ms.openlocfilehash: faa181090efa7c4064a30b42d83afa4888e98b82
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2018
ms.locfileid: "45638479"
---
# <a name="boolean-operators"></a>Boolesche Operatoren

Dieses Thema beschreibt die Unterstützung für boolesche Operatoren in der Sprache F#.

## <a name="summary-of-boolean-operators"></a>Zusammenfassung der booleschen Operatoren

Die folgende Tabelle enthält die booleschen Operatoren, die in F# verfügbar sind. Ist der einzige Typ, der von diesen unterstützt die `bool` Typ.

|Operator|Beschreibung|
|--------|-----------|
|`not`|Boolesche negation|
|<code>&#124;&#124;</code>|Boolesche OR|
|`&&`|Boolesche AND|

Führen Sie die boolesche AND und OR-Operatoren *kurzschlussauswertung*, d. h. sie den Ausdruck auf der rechten Seite des Operators auszuwerten, nur, wenn es um das Gesamtergebnis des Ausdrucks zu bestimmen, die erforderlich ist. Der zweite Ausdruck, der die `&&` Operator wird nur ausgewertet, wenn der erste Ausdruck ergibt `true`; der zweite Ausdruck, der die `||` Operator wird nur ausgewertet, wenn der erste Ausdruck ergibt `false`.

## <a name="see-also"></a>Siehe auch

- [Bitweise Operatoren](bitwise-operators.md)
- [Arithmetische Operatoren](arithmetic-operators.md)
- [Symbol- und Operatorenreferenz](index.md)
