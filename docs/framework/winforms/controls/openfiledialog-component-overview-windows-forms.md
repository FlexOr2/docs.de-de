---
title: Übersicht über die OpenFileDialog-Komponente (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: a49298b2e2cc620ad95e2e0b601a2f49f6ff79d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536077"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>Übersicht über die OpenFileDialog-Komponente (Windows Forms)
Die <xref:System.Windows.Forms.OpenFileDialog>-Komponente von Windows Forms ist ein vorkonfiguriertes Dialogfeld. Er ist der gleiche **Dateiöffnungsmodus** (Dialogfeld), die von Windows-Betriebssystems verfügbar gemacht werden. Die Vererbung erfolgt von der <xref:System.Windows.Forms.CommonDialog>-Klasse.  
  
## <a name="using-this-component"></a>Verwenden diese Komponente  
 Verwenden Sie diese Komponente in der Windows-basierten Anwendung als einfache Lösung für die Dateiauswahl anstatt ein eigenes Dialogfeld zu konfigurieren. Durch die Verwendung von Windows-Standarddialogfeldern erstellen Sie Anwendungen, deren Basisfunktionen Benutzern sofort vertraut sind. Jedoch darüber im Klaren sein, die bei Verwendung der <xref:System.Windows.Forms.OpenFileDialog> -Komponente verwenden, müssen Sie Ihre eigene Logik zum Öffnen von Dateien schreiben.  
  
 Verwenden der <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> Methode, um das Dialogfeld zur Laufzeit anzuzeigen. Sie können Benutzern mit mehreren Dateien geöffnet werden, ermöglichen die <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> Eigenschaft. Darüber hinaus können Sie die <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> Eigenschaft, um zu bestimmen, ob ein Kontrollkästchen schreibgeschützt sind und im Dialogfeld angezeigt wird. Die <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Eigenschaft gibt an, ob das Kontrollkästchen "schreibgeschützt" ausgewählt ist. Schließlich die <xref:System.Windows.Forms.FileDialog.Filter%2A> Eigenschaft legt die aktuelle Filterzeichenfolge für den Namen fest, die im Feld "Dateien des Typs" im Dialogfeld angezeigt werden.  
  
 Wenn sie zu einem Formular hinzugefügt wird die <xref:System.Windows.Forms.OpenFileDialog> Komponente in der Taskleiste am unteren Rand der Windows Forms-Designer angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog-Komponente](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
