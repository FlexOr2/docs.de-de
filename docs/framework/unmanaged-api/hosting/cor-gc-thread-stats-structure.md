---
title: COR_GC_THREAD_STATS-Struktur
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS
helpviewer_keywords: COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10366d183ed7fd7386609e4c5726df0cea4e29a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="033d8-102">COR_GC_THREAD_STATS-Struktur</span><span class="sxs-lookup"><span data-stu-id="033d8-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="033d8-103">Enthält threadspezifische Statistiken zur Garbagecollection.</span><span class="sxs-lookup"><span data-stu-id="033d8-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="033d8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="033d8-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="033d8-105">Member</span><span class="sxs-lookup"><span data-stu-id="033d8-105">Members</span></span>  
  
|<span data-ttu-id="033d8-106">Member</span><span class="sxs-lookup"><span data-stu-id="033d8-106">Member</span></span>|<span data-ttu-id="033d8-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="033d8-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="033d8-108">Die Anzahl der Bytes des Arbeitsspeichers für den Thread, die mit dem aktuellen anfallen `COR_GC_THREAD_STATS` Instanz.</span><span class="sxs-lookup"><span data-stu-id="033d8-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="033d8-109">Diese Zahl ist 0 (null) jedes Mal deaktiviert, tritt eine Generation 0 Garbagecollection auf.</span><span class="sxs-lookup"><span data-stu-id="033d8-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="033d8-110">Die Anzahl der Bytes, die auf eine höhere Generation der letzten Garbagecollection hochgestuft.</span><span class="sxs-lookup"><span data-stu-id="033d8-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="033d8-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="033d8-111">Remarks</span></span>  
 <span data-ttu-id="033d8-112">[ICLRTask:: GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) akzeptiert einen Ausgabeparameter vom Typ `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="033d8-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="033d8-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="033d8-113">Requirements</span></span>  
 <span data-ttu-id="033d8-114">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="033d8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="033d8-115">**Header:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="033d8-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="033d8-116">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="033d8-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="033d8-117">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="033d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="033d8-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="033d8-118">See Also</span></span>  
 [<span data-ttu-id="033d8-119">Hosten von Strukturen</span><span class="sxs-lookup"><span data-stu-id="033d8-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="033d8-120">IHostTask-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="033d8-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)