---
title: '&gt;&gt;-Operator (C#-Referenz)'
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 7a2992befcacfdc1d9bb968b611051e15702cca8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924823"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;-Operator (C#-Referenz)
Der Right Shift-Operator (`>>`) verschiebt den ersten Operanden um die Anzahl von Bits nach rechts, die durch den zweiten Operanden angegeben wird.  
  
## <a name="remarks"></a>Hinweise  
 Ist der erste Operand ein [int](../../../csharp/language-reference/keywords/int.md) oder [uint](../../../csharp/language-reference/keywords/uint.md) (32-Bit-Menge), wird die Umschaltanzahl durch die niederwertigen fünf Bits des zweiten Operanden angegeben (zweiter Operand & 0x1F).  
  
 Ist der erste Operand ein [long](../../../csharp/language-reference/keywords/long.md) oder [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-Bit-Menge), wird die Umschaltanzahl durch die niederwertigen sechs Bits des zweiten Operanden angegeben (zweiter Operand & 0x3F).  
  
 Ist der erste Operand ein [int](../../../csharp/language-reference/keywords/int.md) oder [long](../../../csharp/language-reference/keywords/long.md), handelt es sich bei der Verschiebung nach rechts um eine arithmetische Verschiebung (höherwertige leere Bits werden auf das Vorzeichenbit festgelegt). Ist der erste Operand vom Typ [uint](../../../csharp/language-reference/keywords/uint.md) oder [ulong](../../../csharp/language-reference/keywords/ulong.md), handelt es sich bei der Verschiebung nach rechts um eine logische Verschiebung (höherwertige Bits werden mit Nullen angefüllt).  
  
 Benutzerdefinierte Typen können den `>>`-Operator überladen. Der Typ des ersten Operanden muss daher der benutzerdefinierte Typ sein, der Typ des zweiten Operanden [int](../../../csharp/language-reference/keywords/int.md). Weitere Informationen finden Sie unter [Operator](../../../csharp/language-reference/keywords/operator.md). Wenn ein binärer Operator überladen ist, wird der zugehörige Zuweisungsoperator, sofern er vorhanden ist, auch implizit überladen.  
  
## <a name="example"></a>Beispiel  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a>Siehe auch

- [C#-Referenz](../../../csharp/language-reference/index.md)  
- [C#-Programmierhandbuch](../../../csharp/programming-guide/index.md)  
- [C#-Operatoren](../../../csharp/language-reference/operators/index.md)
