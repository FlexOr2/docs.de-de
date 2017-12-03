---
title: ICorDebugFunction2::SetJMCStatus-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ecbcd5b8171a169fbfdd7175d3d9dfbbcb3855f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a><span data-ttu-id="29662-102">ICorDebugFunction2::SetJMCStatus-Methode</span><span class="sxs-lookup"><span data-stu-id="29662-102">ICorDebugFunction2::SetJMCStatus Method</span></span>
<span data-ttu-id="29662-103">Markiert die Funktion, die von dieser ICorDebugFunction2 dargestellt wird, für nur mein Code schrittweise durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="29662-103">Marks the function represented by this ICorDebugFunction2 for Just My Code stepping.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29662-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="29662-104">Syntax</span></span>  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29662-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="29662-105">Parameters</span></span>  
 `bIsJustMyCode`  
 <span data-ttu-id="29662-106">[in] Legen Sie auf `true` , markieren Sie die Funktion als Benutzercode; legen Sie andernfalls auf `false`.</span><span class="sxs-lookup"><span data-stu-id="29662-106">[in] Set to `true` to mark the function as user code; otherwise, set to `false`.</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="29662-107">Rückgabewerte</span><span class="sxs-lookup"><span data-stu-id="29662-107">Return Values</span></span>  
  
|<span data-ttu-id="29662-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29662-108">HRESULT</span></span>|<span data-ttu-id="29662-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="29662-109">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="29662-110">Die Funktion wurde erfolgreich markiert.</span><span class="sxs-lookup"><span data-stu-id="29662-110">The function was successfully marked.</span></span>|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|<span data-ttu-id="29662-111">Die Funktion kann nicht als Benutzercode gekennzeichnet werden, da es nicht gedebuggt werden kann.</span><span class="sxs-lookup"><span data-stu-id="29662-111">The function could not be marked as user code because it cannot be debugged.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29662-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="29662-112">Remarks</span></span>  
 <span data-ttu-id="29662-113">Nicht-benutzerseitigen Code wird ein nur mein Code zugeordnetem übersprungen wird.</span><span class="sxs-lookup"><span data-stu-id="29662-113">A Just My Code stepper will skip non-user code.</span></span> <span data-ttu-id="29662-114">Benutzercode muss eine Teilmenge von debugfähigem Code.</span><span class="sxs-lookup"><span data-stu-id="29662-114">User code must be a subset of debuggable code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29662-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="29662-115">Requirements</span></span>  
 <span data-ttu-id="29662-116">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29662-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29662-117">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29662-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29662-118">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29662-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29662-119">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29662-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>