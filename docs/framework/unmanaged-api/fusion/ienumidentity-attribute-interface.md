---
title: IEnumIDENTITY_ATTRIBUTE-Schnittstelle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumIDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords: IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f88e400556421e0908e0a0b115f66ec3221124c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="ienumidentityattribute-interface"></a><span data-ttu-id="0041f-102">IEnumIDENTITY_ATTRIBUTE-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="0041f-102">IEnumIDENTITY_ATTRIBUTE Interface</span></span>
<span data-ttu-id="0041f-103">Dient als Enumerator für die Attribute des Codeobjekts im aktuellen Bereich.</span><span class="sxs-lookup"><span data-stu-id="0041f-103">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0041f-104">Methoden</span><span class="sxs-lookup"><span data-stu-id="0041f-104">Methods</span></span>  
  
|<span data-ttu-id="0041f-105">Methode</span><span class="sxs-lookup"><span data-stu-id="0041f-105">Method</span></span>|<span data-ttu-id="0041f-106">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0041f-106">Description</span></span>|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|<span data-ttu-id="0041f-107">Ruft einen Schnittstellenzeiger auf eine neue `IEnumIDENTITY_ATTRIBUTE` , enthält das dieselben Member wie dies `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="0041f-107">Gets an interface pointer to a new `IEnumIDENTITY_ATTRIBUTE` that contains the same members as this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|<span data-ttu-id="0041f-108">Schreibt die Daten in die Elemente dieser `IEnumIDENTITY_ATTRIBUTE` auf den angegebenen Datenpuffer.</span><span class="sxs-lookup"><span data-stu-id="0041f-108">Writes the data contained in the elements of this `IEnumIDENTITY_ATTRIBUTE` to the specified data buffer.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|<span data-ttu-id="0041f-109">Ruft die angegebene Anzahl von Attributen, beginnend mit der aktuellen Position ab.</span><span class="sxs-lookup"><span data-stu-id="0041f-109">Gets the specified number of attributes, starting at the current position.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|<span data-ttu-id="0041f-110">Verschiebt den Anweisungszeiger an den Anfang `IEnumIDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="0041f-110">Moves the instruction pointer to the beginning of this `IEnumIDENTITY_ATTRIBUTE`.</span></span>|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|<span data-ttu-id="0041f-111">Verschiebt den Anweisungszeiger vorwärts durch die angegebene Anzahl von Elementen, die an der aktuellen Position ab.</span><span class="sxs-lookup"><span data-stu-id="0041f-111">Moves the instruction pointer forward by the specified number of elements, starting at the current position.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0041f-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0041f-112">Requirements</span></span>  
 <span data-ttu-id="0041f-113">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0041f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0041f-114">**Header:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="0041f-114">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0041f-115">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0041f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0041f-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0041f-116">See Also</span></span>  
 [<span data-ttu-id="0041f-117">Fusion-Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="0041f-117">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)