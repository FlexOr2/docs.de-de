---
title: 'Gewusst wie: Schützen eines Prozedurarguments gegen Wertänderungen (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 393127353a020c1db5df3011b2a97b1c53097f27
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50035643"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>Gewusst wie: Schützen eines Prozedurarguments gegen Wertänderungen (Visual Basic)
Wenn eine Prozedur einen Parameter als [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic bietet der Code der Prozedur einen direkten Verweis auf das Programmierelement zugrunde liegenden Arguments im aufrufenden Code. Dies ermöglicht das Verfahren zum Ändern des Werts, der dem Argument im aufrufenden Code zugrunde liegt. In einigen Fällen kann der aufrufende Code eine solche Änderung schützen möchten.  
  
 Sie können immer ein Argument aus schützen, indem der entsprechende Parameter deklarieren [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in der Prozedur. Wenn Sie ein bestimmtes Argument in einigen Fällen aber in anderen ändern möchten, deklarieren Sie es `ByRef` und lassen Sie den aufrufenden Code, der den Übergabemechanismus bei jedem Aufruf zu bestimmen. Hierzu setzen Sie das entsprechende Argument in Klammern einschließen, um es als Wert übergeben, oder setzt ihn nicht in Klammern einschließen, um es als Verweis zu übergeben. Weitere Informationen finden Sie unter [Vorgehensweise: erzwingen, dass ein Argument als Wert übergeben werden](./how-to-force-an-argument-to-be-passed-by-value.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt zwei Verfahren, die eine Arrayvariable und ausgeführt werden, die Elemente. Die `increase` Verfahren einfach zu jedem Element hinzufügt. Die `replace` Prozedur weist ein neues Array, an den Parameter `a()` , und klicken Sie dann auf die einzelnen Elemente hinzugefügt. Die neuzuweisung wirkt sich jedoch nicht auf die zugrunde liegende Arrayvariable im aufrufenden Code aus.  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 Die erste `MsgBox` aufrufen, zeigt "nach increase(n):: 11", "21", "31", "41". Da das Array `n` ist ein Verweistyp, `increase` können ihre Member, ändern, auch wenn der Übergabemechanismus ist `ByVal`.  
  
 Die zweite `MsgBox` aufrufen, zeigt "nach Replace(n):: 11", "21", "31", "41". Da `n` übergeben `ByVal`, `replace` die Variable kann nicht geändert werden `n` im aufrufenden Code, indem Sie ein neues Array zuweisen. Wenn `replace` neuen Arrayinstanz erstellt `k` und weist sie auf die lokale Variable `a`, er verliert den Verweis auf `n` vom aufrufenden Code übergeben. Wenn sie die Mitglieder der ändert `a`, nur das lokale Array `k` betroffen ist. Aus diesem Grund `replace` erhöht sich die Werte des Arrays nicht `n` im aufrufenden Code.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Der Standardwert in Visual Basic ist, Argumente als Wert übergeben. Allerdings ist es guter Programmierstil, auch die [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) oder [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) Schlüsselwort für jeden deklarierten Parameter. Dadurch wird Ihr Code einfacher zu lesen.  
  
## <a name="see-also"></a>Siehe auch  
 [Verfahren](./index.md)  
 [Parameter und Argumente von Prozeduren](./procedure-parameters-and-arguments.md)  
 [Gewusst wie: Übergeben von Argumenten an eine Prozedur](./how-to-pass-arguments-to-a-procedure.md)  
 [Übergeben von Argumenten als Wert und als Verweis](./passing-arguments-by-value-and-by-reference.md)  
 [Unterschiede zwischen veränderbaren und nicht veränderbaren Argumenten](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [Unterschiede zwischen dem Übergeben von Argumenten als Wert und als Verweis](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Gewusst wie: Ändern des Werts eines Prozedurarguments](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Gewusst wie: Erzwingen, dass ein Argument als Wert übergeben wird](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Übergeben von Argumenten nach Position und Name](./passing-arguments-by-position-and-by-name.md)  
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
