---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6331a55bb1d20b5804605db103dcfd2997e348d9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930441"
---
# <a name="-baseaddress"></a>-baseaddress
Gibt einen Standard-Basisadresse an, beim Erstellen einer DLL.  
  
## <a name="syntax"></a>Syntax  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumente  
  
|Begriff|Definition|  
|---|---|  
|`address`|Erforderlich. Die Basisadresse für die DLL. Diese Adresse muss als hexadezimale Zahl angegeben werden.|  
  
## <a name="remarks"></a>Hinweise  
 Die Standard-Basisadresse für eine DLL-Datei wird festgelegt, durch die [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Denken Sie daran, dass das niederwertige Wort in dieser Adresse gerundet wird. Wenn Sie 0 x 11110001 angeben, wird es beispielsweise auf 0 x 11110000 gerundet.  
  
 Um die Signatur für eine DLL abzuschließen, verwenden Sie die `–R` Möglichkeit, das Strong Name-Tool (Sn.exe).  
  
 Diese Option wird ignoriert, wenn das Ziel nicht um eine DLL-Datei ist.  
  
|-Baseaddress in Visual Studio-IDE festlegen|  
|---|  
|1.  Ein Projekt auswählen in **Projektmappen-Explorer**. Klicken Sie im Menü **Projekt** auf **Eigenschaften**. <br />2.  Klicken Sie auf die Registerkarte **Kompilieren**.<br />3.  Klicken Sie auf **erweiterte**.<br />4.  Ändern Sie den Wert in der **DLL-Basisadresse:** Feld. **Hinweis:** der **DLL-Basisadresse:** Feld ist schreibgeschützt, es sei denn, das Ziel eine DLL-Datei ist.|  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Basic-Befehlszeilencompiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Beispiele für Kompilierungsbefehlszeilen](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (Strong Name-Tool)] [Sn.exe (Strong Name-Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))
