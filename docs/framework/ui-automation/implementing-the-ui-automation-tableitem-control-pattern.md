---
title: Implementieren des TableItem-Steuerelementmusters der Benutzeroberflächenautomatisierung
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: e5d5e82c5c2cfc48c98559bd6ce14519bdfaa522
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196556"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>Implementieren des TableItem-Steuerelementmusters der Benutzeroberflächenautomatisierung
> [!NOTE]
>  Diese Dokumentation ist für .NET Framework-Entwickler vorgesehen, die die verwalteten [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-Klassen verwenden möchten, die im <xref:System.Windows.Automation>-Namespace definiert sind. Die neuesten Informationen zu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], finden Sie unter [Windows-Automatisierungs-API: UI-Automatisierung](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Dieses Thema enthält Richtlinien und Konventionen zum Implementieren von <xref:System.Windows.Automation.Provider.ITableItemProvider>, einschließlich Informationen über Ereignisse und Eigenschaften. Links zu zusätzlichen Referenzen sind am Ende dieser Übersicht aufgelistet.  
  
 Die <xref:System.Windows.Automation.TableItemPattern> -Steuerelementmuster wird verwendet, um untergeordnete Steuerelemente von Containern zu unterstützen, implementieren <xref:System.Windows.Automation.Provider.ITableProvider>. Der Zugriff auf Funktionen einzelner Zellen wird bereitgestellt, durch die erforderlichen gleichzeitigen Implementierung von <xref:System.Windows.Automation.Provider.IGridItemProvider>. Dieses Steuerelementmuster ist analog zu <xref:System.Windows.Automation.Provider.IGridItemProvider> mit dem Unterschied, dass jedes implementieren Steuerelement <xref:System.Windows.Automation.Provider.ITableItemProvider> müssen, die Beziehung zwischen den einzelnen Zelle und die Zeilen- und programmgesteuert verfügbar machen. Beispiele für Steuerelemente, die dieses Steuerelementmuster implementieren, finden Sie unter [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementierungsrichtlinien und -konventionen  
  
-   Funktionen des zugehörigen Rasters-Element, finden Sie unter [implementieren das GridItem-Steuerelementmusters der Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md).  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>Erforderliche Member für ITableItemProvider  
  
|Erforderlicher Member|Memberart|Hinweise|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|Methode|Keiner|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|Methode|Keiner|  
  
 Diesem Steuerelementmuster sind keine Eigenschaften oder Ereignisse zugeordnet.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Ausnahmen  
 Diesem Steuerelementmuster sind keine Ausnahmen zugeordnet.  
  
## <a name="see-also"></a>Siehe auch  
 [Übersicht über Steuerelementmuster für Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Unterstützung von Steuerelementmustern in einem Benutzeroberflächenautomatisierungs-Anbieter](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Steuerelementmuster für Benutzeroberflächenautomatisierung für Clients](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementieren des Table-Steuerelementmusters der Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)  
 [Implementieren des GridItem-Steuerelementmusters der Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [Übersicht über die Benutzeroberflächenautomatisierungs-Struktur](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Verwenden der Zwischenspeicherung in der Benutzeroberflächenautomatisierung](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
