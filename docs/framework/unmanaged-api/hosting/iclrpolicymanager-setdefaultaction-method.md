---
title: ICLRPolicyManager::SetDefaultAction-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRPolicyManager.SetDefaultAction
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ecc2e35433a1021e230b45adddf3bede055d3dfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a><span data-ttu-id="e9c4f-102">ICLRPolicyManager::SetDefaultAction-Methode</span><span class="sxs-lookup"><span data-stu-id="e9c4f-102">ICLRPolicyManager::SetDefaultAction Method</span></span>
<span data-ttu-id="e9c4f-103">Gibt die Richtlinienaktion, die die common Language Runtime (CLR) ausführen sollten, wenn der angegebene Vorgang auftritt.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9c4f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e9c4f-104">Syntax</span></span>  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9c4f-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="e9c4f-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="e9c4f-106">[in] Eines der [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) Werte, der die Aktion, für welche CLR Verhalten angepasst werden soll.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the action for which CLR behavior should be customized.</span></span>  
  
 `action`  
 <span data-ttu-id="e9c4f-107">[in] Eines der [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) Werte, der die Richtlinienaktion CLR abwartet, wenn `operation` auftritt.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-107">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9c4f-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e9c4f-108">Return Value</span></span>  
  
|<span data-ttu-id="e9c4f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9c4f-109">HRESULT</span></span>|<span data-ttu-id="e9c4f-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="e9c4f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9c4f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9c4f-111">S_OK</span></span>|<span data-ttu-id="e9c4f-112">`SetDefaultAction`wurde erfolgreich zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-112">`SetDefaultAction` returned successfully.</span></span>|  
|<span data-ttu-id="e9c4f-113">HOST_E_CLRNOTAVAILABLE ZURÜCK</span><span class="sxs-lookup"><span data-stu-id="e9c4f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9c4f-114">Die CLR wurde nicht in einen Prozess geladen, oder die CLR wird in einem Zustand, in dem er nicht verwalteten Code ausführen oder den Aufruf erfolgreich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9c4f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9c4f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9c4f-116">Der Aufruf ist ein Timeout aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-116">The call timed out.</span></span>|  
|<span data-ttu-id="e9c4f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9c4f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9c4f-118">Der Aufrufer ist nicht Besitzer der Sperre.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9c4f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9c4f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9c4f-120">Ein Ereignis wurde abgebrochen, während ein blockierten Thread oder eine Fiber darauf gewartet.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9c4f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9c4f-121">E_FAIL</span></span>|<span data-ttu-id="e9c4f-122">Ein Unbekannter Schwerwiegender Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9c4f-123">Nachdem eine Methode E_FAIL zurückgegeben hat, ist die CLR nicht mehr verwendbar innerhalb des Prozesses.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9c4f-124">Nachfolgende Aufrufe zum Hosten der Methoden HOST_E_CLRNOTAVAILABLE zurück.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e9c4f-125">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e9c4f-125">E_INVALIDARG</span></span>|<span data-ttu-id="e9c4f-126">Eine ungültige `action` wurde angegeben, für die `operation`, oder für wurde ein ungültiger Wert angegeben `operation`.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-126">An invalid `action` was specified for the `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9c4f-127">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e9c4f-127">Remarks</span></span>  
 <span data-ttu-id="e9c4f-128">Nicht alle Werte für Aktivierungsrichtlinien Aktion können als das Standardverhalten für CLR-Vorgänge angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-128">Not all policy action values can be specified as the default behavior for CLR operations.</span></span> <span data-ttu-id="e9c4f-129">`SetDefaultAction`kann nur für eskalieren Sie das Verhalten in der Regel verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-129">`SetDefaultAction` can typically be used only to escalate behavior.</span></span> <span data-ttu-id="e9c4f-130">Ein Host kann z. B. angeben, die Threadabbrüche in grobe aktiviert werden thread-Abbrüche, jedoch nicht das Gegenteil.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-130">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="e9c4f-131">Die folgende Tabelle beschreibt die gültigen `action` Werte für jeden möglichen `operation` Wert.</span><span class="sxs-lookup"><span data-stu-id="e9c4f-131">The table below describes the valid `action` values for each possible `operation` value.</span></span>  
  
|<span data-ttu-id="e9c4f-132">Wert für`operation`</span><span class="sxs-lookup"><span data-stu-id="e9c4f-132">Value for `operation`</span></span>|<span data-ttu-id="e9c4f-133">Gültige Werte für`action`</span><span class="sxs-lookup"><span data-stu-id="e9c4f-133">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="e9c4f-134">OPR_ThreadAbort</span><span class="sxs-lookup"><span data-stu-id="e9c4f-134">OPR_ThreadAbort</span></span>|<span data-ttu-id="e9c4f-135">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="e9c4f-135">-   eAbortThread</span></span><br /><span data-ttu-id="e9c4f-136">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e9c4f-136">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e9c4f-137">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-137">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-138">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-138">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-139">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-139">-   eExitProcess</span></span><br /><span data-ttu-id="e9c4f-140">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-140">-   eFastExitProcess</span></span><br /><span data-ttu-id="e9c4f-141">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-141">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e9c4f-142">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e9c4f-142">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e9c4f-143">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e9c4f-143">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="e9c4f-144">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="e9c4f-144">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="e9c4f-145">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e9c4f-145">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e9c4f-146">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-146">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-147">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-147">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-148">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-148">-   eExitProcess</span></span><br /><span data-ttu-id="e9c4f-149">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-149">-   eFastExitProcess</span></span><br /><span data-ttu-id="e9c4f-150">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-150">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e9c4f-151">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e9c4f-151">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e9c4f-152">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="e9c4f-152">OPR_AppDomainUnload</span></span>|<span data-ttu-id="e9c4f-153">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-153">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-154">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-154">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-155">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-155">-   eExitProcess</span></span><br /><span data-ttu-id="e9c4f-156">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-156">-   eFastExitProcess</span></span><br /><span data-ttu-id="e9c4f-157">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-157">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e9c4f-158">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e9c4f-158">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e9c4f-159">OPR_AppDomainRudeUnload</span><span class="sxs-lookup"><span data-stu-id="e9c4f-159">OPR_AppDomainRudeUnload</span></span>|<span data-ttu-id="e9c4f-160">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-160">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-161">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-161">-   eExitProcess</span></span><br /><span data-ttu-id="e9c4f-162">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-162">-   eFastExitProcess</span></span><br /><span data-ttu-id="e9c4f-163">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-163">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e9c4f-164">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e9c4f-164">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e9c4f-165">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="e9c4f-165">OPR_ProcessExit</span></span>|<span data-ttu-id="e9c4f-166">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-166">-   eExitProcess</span></span><br /><span data-ttu-id="e9c4f-167">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-167">-   eFastExitProcess</span></span><br /><span data-ttu-id="e9c4f-168">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-168">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e9c4f-169">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e9c4f-169">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="e9c4f-170">OPR_FinalizerRun</span><span class="sxs-lookup"><span data-stu-id="e9c4f-170">OPR_FinalizerRun</span></span>|<span data-ttu-id="e9c4f-171">-eNoAction</span><span class="sxs-lookup"><span data-stu-id="e9c4f-171">-   eNoAction</span></span><br /><span data-ttu-id="e9c4f-172">-eAbortThread</span><span class="sxs-lookup"><span data-stu-id="e9c4f-172">-   eAbortThread</span></span><br /><span data-ttu-id="e9c4f-173">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="e9c4f-173">-   eRudeAbortThread</span></span><br /><span data-ttu-id="e9c4f-174">-eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-174">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-175">-eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="e9c4f-175">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="e9c4f-176">-eExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-176">-   eExitProcess</span></span><br /><span data-ttu-id="e9c4f-177">-eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-177">-   eFastExitProcess</span></span><br /><span data-ttu-id="e9c4f-178">-eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="e9c4f-178">-   eRudeExitProcess</span></span><br /><span data-ttu-id="e9c4f-179">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="e9c4f-179">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e9c4f-180">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e9c4f-180">Requirements</span></span>  
 <span data-ttu-id="e9c4f-181">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9c4f-181">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9c4f-182">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9c4f-182">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9c4f-183">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="e9c4f-183">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9c4f-184">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9c4f-184">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c4f-185">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e9c4f-185">See Also</span></span>  
 [<span data-ttu-id="e9c4f-186">EClrOperation-Enumeration</span><span class="sxs-lookup"><span data-stu-id="e9c4f-186">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="e9c4f-187">EPolicyAction-Enumeration</span><span class="sxs-lookup"><span data-stu-id="e9c4f-187">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="e9c4f-188">ICLRPolicyManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="e9c4f-188">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)