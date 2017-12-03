---
title: ICorDebugAppDomainEnum::Next-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10d53ebac99942ac9376041f217df53965bdbb2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="fc6b0-102">ICorDebugAppDomainEnum::Next-Methode</span><span class="sxs-lookup"><span data-stu-id="fc6b0-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="fc6b0-103">Ruft die angegebene Anzahl von Anwendungsdomänen aus der Auflistung, beginnend mit der aktuellen Cursorposition ab.</span><span class="sxs-lookup"><span data-stu-id="fc6b0-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc6b0-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fc6b0-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc6b0-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="fc6b0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="fc6b0-106">[in] Die Anzahl der Anwendungsdomänen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="fc6b0-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="fc6b0-107">[out] Ein Array von Zeigern, von denen jedes auf ein ICorDebugAppDomain-Objekt verweist, der eine Anwendungsdomäne darstellt.</span><span class="sxs-lookup"><span data-stu-id="fc6b0-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="fc6b0-108">[out] Ein Zeiger auf die Anzahl der tatsächlich zurückgegebenen Anwendungsdomänen.</span><span class="sxs-lookup"><span data-stu-id="fc6b0-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="fc6b0-109">Dieser Wert kann null sein, wenn `celt` ist ein.</span><span class="sxs-lookup"><span data-stu-id="fc6b0-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc6b0-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="fc6b0-110">Requirements</span></span>  
 <span data-ttu-id="fc6b0-111">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc6b0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc6b0-112">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc6b0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc6b0-113">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc6b0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc6b0-114">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc6b0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>