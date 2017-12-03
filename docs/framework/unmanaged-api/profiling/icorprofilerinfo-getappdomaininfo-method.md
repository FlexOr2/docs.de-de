---
title: ICorProfilerInfo::GetAppDomainInfo-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAppDomainInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c31d3c61a868bf741213f6e505d91524cc925207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="e0bcc-102">ICorProfilerInfo::GetAppDomainInfo-Methode</span><span class="sxs-lookup"><span data-stu-id="e0bcc-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="e0bcc-103">Akzeptiert eine Anwendungsdomänen-ID.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-103">Accepts an application domain ID.</span></span> <span data-ttu-id="e0bcc-104">Gibt den Namen einer Anwendungsdomäne und die ID des Prozesses zurück, in dem diese enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bcc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0bcc-105">Syntax</span></span>  
  
```  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0bcc-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="e0bcc-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="e0bcc-107">[in] Die ID der Anwendungsdomäne.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="e0bcc-108">[in] Die Länge des `szName`-Rückgabepuffers in Zeichen.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e0bcc-109">[out] Ein Zeiger auf die Gesamtzeichenanzahl des Namens der Anwendungsdomäne.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e0bcc-110">[out] Ein vom Aufrufer bereitgestellter Breitzeichenpuffer.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="e0bcc-111">Wenn die Methode abgeschlossen ist, enthält `szName` den vollständigen oder teilweisen Anwendungsdomänennamen.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="e0bcc-112">[out] Ein Zeiger auf die ID Prozesses, der die Anwendungsdomäne enthält.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0bcc-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e0bcc-113">Remarks</span></span>  
 <span data-ttu-id="e0bcc-114">Nachdem diese Methode abgeschlossen ist, müssen Sie überprüfen, ob der `szName`-Puffer groß genug war, um den vollständigen Namen der Anwendungsdomäne aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="e0bcc-115">Vergleichen Sie hierzu den Wert, auf den `pcchName` verweist, mit dem Wert des `cchName`-Parameters.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="e0bcc-116">Wenn `pcchName` auf einen Wert verweist, der größer als `cchName` ist, weisen Sie einen größeren `szName`-Puffer zu, aktualisieren Sie `cchName` mit der neuen Größe, und rufen Sie `GetAppDomainInfo` erneut auf.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="e0bcc-117">Alternativ können Sie zuerst `GetAppDomainInfo` mit einem `szName`-Puffer der Länge 0 (null) aufrufen, um die richtige Puffergröße zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="e0bcc-118">Sie können die Puffergröße dann auf den Wert festlegen, der von `pcchName` zurückgegeben wurde, und `GetAppDomainInfo` erneut aufrufen.</span><span class="sxs-lookup"><span data-stu-id="e0bcc-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0bcc-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e0bcc-119">Requirements</span></span>  
 <span data-ttu-id="e0bcc-120">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0bcc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0bcc-121">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0bcc-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0bcc-122">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0bcc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0bcc-123">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0bcc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bcc-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e0bcc-124">See Also</span></span>  
 [<span data-ttu-id="e0bcc-125">ICorProfilerInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="e0bcc-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="e0bcc-126">Profilerstellungsschnittstellen</span><span class="sxs-lookup"><span data-stu-id="e0bcc-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e0bcc-127">Profilerstellung</span><span class="sxs-lookup"><span data-stu-id="e0bcc-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)