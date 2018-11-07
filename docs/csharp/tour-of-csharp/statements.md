---
title: C#-Anweisungen – Überblick über C#
description: Sie erstellen die Aktionen eines C#-Programms mit Anweisungen.
ms.date: 11/06/2016
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.openlocfilehash: 2f25c07ccc0af27a503465b9414bf607c61d1b2e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351978"
---
# <a name="statements"></a>Anweisungen

Die Aktionen eines Programms werden mit *Anweisungen* ausgedrückt. C# unterstützt verschiedene Arten von Anweisungen, von denen ein Teil als eingebettete Anweisungen definiert ist.

Ein *Block* ermöglicht, mehrere Anweisungen in Kontexten zu schreiben, in denen eine einzelne Anweisung zulässig ist. Ein Block besteht aus einer Liste von Anweisungen, die zwischen den Trennzeichen `{` und `}` geschrieben sind.

*Deklarationsanweisungen* werden verwendet, um lokale Variablen und Konstanten deklarieren.

*Ausdrucksanweisungen* werden zum Auswerten von Ausdrücken verwendet. Ausdrücke, die als Anweisungen verwendet werden können, enthalten Methodenaufrufe, Objektzuordnungen mit dem `new`-Operator, Zuweisungen mit `=` und den Verbundzuweisungsoperatoren, Inkrementier- und Dekrementiervorgänge unter Verwendung des `++`- und `--`-Operators und `await`-Ausdrücke.

*Auswahlanweisungen* werden verwendet, um eine Anzahl von möglichen Anweisungen für die Ausführung anhand des Werts eines Ausdrucks auszuwählen. Zu dieser Gruppe gehören die `if`- und `switch`-Anweisungen.

*Iterationsanweisungen* werden verwendet, um eine eingebettete Anweisung wiederholt auszuführen. Zu dieser Gruppe gehören die `while`-, `do`-, `for`- und `foreach`-Anweisungen.

*Sprunganweisungen* werden verwendet, um die Steuerung zu übertragen. Zu dieser Gruppe gehören die `break`-, `continue`-, `goto`-, `throw`-, `return`- und `yield`-Anweisungen.

Mit der `try`... `catch`-Anweisung werden Ausnahmen abgefangen, die während der Ausführung eines Blocks auftreten, und mit der `try`... `finally`-Anweisung wird Finalisierungscode angegeben, der immer ausgeführt wird, unabhängig davon, ob eine Ausnahme aufgetreten ist oder nicht.

Mit den Anweisungen `checked` und `unchecked` wird der Überlaufüberprüfungs-Kontext für arithmetische Operationen für Ganzzahltypen und Konvertierungen gesteuert.

Die `lock`-Anweisung wird verwendet, um die Sperre für gegenseitigen Ausschluss für ein bestimmtes Objekt abzurufen, eine Anweisung auszuführen und die Sperre aufzuheben.

Die `using`-Anweisung wird verwendet, um eine Ressource abzurufen, eine Anweisung auszuführen und dann diese Ressource zu verwerfen.

Im Folgenden werden die Arten von Anweisungen aufgelistet, die verwendet werden können, und für jede ein Beispiel aufgeführt.

* Deklaration lokaler Variablen:

 [!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L8-L14)]

* Deklaration lokaler Konstanten:

 [!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L16-L21)]

* Ausdrucksanweisung:

 [!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L23-L30)]

* `if`-Anweisung:

 [!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L32-L42)]

* `switch`-Anweisung:

 [!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L44-L59)]

* `while`-Anweisung:

 [!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L61-L69)]

* `do`-Anweisung:

 [!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L71-L80)]

* `for`-Anweisung:

 [!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L82-L88)]

* `foreach`-Anweisung:

 [!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L90-L96)]

* `break`-Anweisung:

 [!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L98-L107)]

* `continue`-Anweisung:

 [!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L109-L117)]

* `goto`-Anweisung:

 [!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L119-L128)]

* `return`-Anweisung:

 [!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L130-L138)]

* `yield`-Anweisung:

 [!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L140-L154)]

* `throw`-Anweisungen und `try`-Anweisungen:

 [!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L156-L182)]

* `checked`- und `unchecked`-Anweisungen:

 [!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L184-L195)]

* `lock`-Anweisung:

 [!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L256-L272)]

* `using`-Anweisung:

 [!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L197-L205)]

>[!div class="step-by-step"]
[Zurück](expressions.md)
[Weiter](classes-and-objects.md)
