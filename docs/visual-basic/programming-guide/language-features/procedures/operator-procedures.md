---
title: Operatorprozeduren (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: 5b4641ce8509e3111a11ed803d36194d5a301bce
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805710"
---
# <a name="operator-procedures-visual-basic"></a>Operatorprozeduren (Visual Basic)
Eine Operatorprozedur besteht aus einer Reihe von Visual Basic-Anweisungen, die das Verhalten eines standard-Operators definieren (z. B. `*`, `<>`, oder `And`) für eine Klasse oder Struktur, die Sie definiert haben. Dies wird auch bezeichnet *operatorüberladung*.  
  
## <a name="when-to-define-operator-procedures"></a>Beim Definieren von Operatorprozeduren  
 Wenn Sie eine Klasse oder Struktur definiert haben, können Sie Variablen des Typs der betreffenden Klasse oder Struktur deklarieren. In einigen Fällen muss eine solche Variable zur Teilnahme an eines Vorgangs als Teil eines Ausdrucks ein. Zu diesem Zweck müssen sie ein Operand eines Operators sein.  
  
 Visual Basic definiert nur die grundlegenden Datentypen von Operatoren. Sie können das Verhalten eines Operators, wenn bei mindestens einem definieren oder beide Operanden vom Typ der Klasse oder Struktur sind.  
  
 Weitere Informationen finden Sie unter [Operator-Anweisung](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="types-of-operator-procedure"></a>Typen von Operatorprozedur  
 Eine Operatorprozedur kann einer der folgenden Typen sein:  
  
-   Eine Definition eines unären Operators, in dem das Argument den Typ der Klasse oder Struktur ist.  
  
-   Eine Definition eines binären Operators, in denen mindestens eines der Argumente des Typs der Klasse oder Struktur ist.  
  
-   Eine Definition eines Konvertierungsoperators, der den Typ der Klasse oder Struktur, in dem das Argument ist.  
  
-   Eine Definition eines Konvertierungsoperators, der den Typ der Klasse oder Struktur zurückgibt.  
  
 Konvertierungsoperatoren sind immer unär, und verwenden Sie Sie immer `CType` wie der Operator, die Sie definieren.  
  
## <a name="declaration-syntax"></a>Deklarationssyntax  
 Die Syntax zum Deklarieren einer Operatorprozedur lautet wie folgt:  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  *Operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *Datatype*  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 Verwenden Sie die `Widening` oder `Narrowing` -Schlüsselwort wird nur für einen Operator für die Konvertierung. Das Operatorsymbol ist immer [CType-Funktion](../../../../visual-basic/language-reference/functions/ctype-function.md) für einen Operator für die Konvertierung.  
  
 Deklarieren Sie zwei Operanden in einen binären Operator definieren, und deklarieren Sie ein Operand einen unäroperator, einschließlich eines Konvertierungsoperators Typ definieren. Alle Operanden müssen deklariert werden `ByVal`.  
  
 Sie deklarieren alle Operanden auf die gleiche Weise, die Sie deklarieren die Parameter für [Sub-Prozeduren](./sub-procedures.md).  
  
### <a name="data-type"></a>Datentyp  
 Da Sie für eine Klasse oder Struktur, die Sie definiert haben, einen Operator definieren, muss mindestens einer der Operanden des Datentyps der betreffenden Klasse oder Struktur sein. Für einen Typkonvertierungsoperator muss der Operand oder der Rückgabetyp des Datentyps der Klasse oder Struktur sein.  
  
 Weitere Informationen finden Sie unter [Operator-Anweisung](../../../../visual-basic/language-reference/statements/operator-statement.md).  
  
## <a name="calling-syntax"></a>Aufrufen der Syntax  
 Sie aufrufen eine Operatorprozedur implizit mit dem Symbol "Operator" in einem Ausdruck. Sie geben die Operanden der genauso wie für die vordefinierten Operatoren verwenden.  
  
 Die Syntax für einen impliziten Aufruf einer Operatorprozedur lautet wie folgt:  
  
 `Dim testStruct As`  *Strukturname*  
  
 `Dim testNewStruct As`  *Strukturname*`= testStruct`*Operatorsymbol*  `10`  
  
### <a name="illustration-of-declaration-and-call"></a>Abbildung der Deklaration und Aufruf  
 Die folgende Struktur speichert einen 128-Bit-Ganzzahl mit Vorzeichen-Wert als die höherwertigen und niederwertige Bestandteile. Definiert die `+` Operator, um zwei `veryLong` Werte und generiert eine resultierende `veryLong` Wert.  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 Das folgende Beispiel zeigt einen typischen Aufruf der `+` für definierten Operator `veryLong`.  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 Weitere Informationen und Beispiele finden Sie unter [Operator Overloading in Visual Basic 2005 (Operatorüberladung in Visual Basic 2005)](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).  
  
## <a name="see-also"></a>Siehe auch  
 [Verfahren](./index.md)  
 [Sub-Prozeduren](./sub-procedures.md)  
 [Function-Prozeduren](./function-procedures.md)  
 [Eigenschaftenprozeduren](./property-procedures.md)  
 [Parameter und Argumente von Prozeduren](./procedure-parameters-and-arguments.md)  
 [Operator-Anweisung](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Gewusst wie: Definieren eines Operators](./how-to-define-an-operator.md)  
 [Gewusst wie: Definieren eines Konvertierungsoperators](./how-to-define-a-conversion-operator.md)  
 [Gewusst wie: Aufrufen einer Operatorprozedur](./how-to-call-an-operator-procedure.md)  
 [Gewusst wie: Verwenden einer Klasse, die Operatoren definiert](./how-to-use-a-class-that-defines-operators.md)
