---
title: ClrCreateManagedInstance-Funktion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: ClrCreateManagedInstance
helpviewer_keywords: ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d27a881f84121f0d096eae7c693dec5b674caec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="1b0be-102">ClrCreateManagedInstance-Funktion</span><span class="sxs-lookup"><span data-stu-id="1b0be-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="1b0be-103">Erstellt eine Instanz des angegebenen verwalteten Typs.</span><span class="sxs-lookup"><span data-stu-id="1b0be-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="1b0be-104">Diese Funktion ist in [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] veraltet.</span><span class="sxs-lookup"><span data-stu-id="1b0be-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="1b0be-105">COM-Aktivierung verwenden, um eine Instanz des verwalteten Typs zu erstellen, oder verwenden Sie die hosten (finden Sie unter [CLR Hosten von Schnittstellen hinzugefügt, in der .NET Framework 4 und 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span><span class="sxs-lookup"><span data-stu-id="1b0be-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b0be-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b0be-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b0be-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="1b0be-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="1b0be-108">[in] Ein Zeiger auf den Namen des Instanztyps angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="1b0be-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="1b0be-109">[in] Die `IID` des Instanztyps angefordert wird.</span><span class="sxs-lookup"><span data-stu-id="1b0be-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="1b0be-110">[out] Ein Zeiger auf einen Zeiger auf eine Instanz des verwalteten Typs, der vom Aufrufer angefordert wurde.</span><span class="sxs-lookup"><span data-stu-id="1b0be-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b0be-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1b0be-111">Remarks</span></span>  
 <span data-ttu-id="1b0be-112">Die common Language Runtime sollte bereits in einen Prozess geladen werden.</span><span class="sxs-lookup"><span data-stu-id="1b0be-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="1b0be-113">Es kann z. B. geladen werden, mithilfe eines Aufrufs an die [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) Funktion vor der `ClrCreateManagedInstance` Funktion wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="1b0be-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="1b0be-114">Wenn die Common Language Runtime nicht geladen wurde, `ClrCreateManagedInstance` versucht zuerst, Version 1.0.3705 der Laufzeit zu laden.</span><span class="sxs-lookup"><span data-stu-id="1b0be-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="1b0be-115">Wenn dies fehlschlägt, versucht, die neueste Version der Laufzeit laden.</span><span class="sxs-lookup"><span data-stu-id="1b0be-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b0be-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1b0be-116">Requirements</span></span>  
 <span data-ttu-id="1b0be-117">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b0be-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b0be-118">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b0be-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b0be-119">**Bibliothek:** "Mscoree.dll"</span><span class="sxs-lookup"><span data-stu-id="1b0be-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b0be-120">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b0be-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b0be-121">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1b0be-121">See Also</span></span>  
 [<span data-ttu-id="1b0be-122">Veraltete CLR-Hostingfunktionen</span><span class="sxs-lookup"><span data-stu-id="1b0be-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="1b0be-123">Hosting</span><span class="sxs-lookup"><span data-stu-id="1b0be-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)