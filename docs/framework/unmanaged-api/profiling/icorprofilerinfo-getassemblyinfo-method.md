---
title: ICorProfilerInfo::GetAssemblyInfo-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetAssemblyInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d4eab4a4bfbf91fd86a3742600f3383a8d374905
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="ee531-102">ICorProfilerInfo::GetAssemblyInfo-Methode</span><span class="sxs-lookup"><span data-stu-id="ee531-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="ee531-103">Akzeptiert eine Assembly-ID und gibt den Namen der Assembly und die ID ihres Manifestmoduls zurück.</span><span class="sxs-lookup"><span data-stu-id="ee531-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee531-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee531-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee531-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="ee531-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="ee531-106">[in] Der Bezeichner der Assembly.</span><span class="sxs-lookup"><span data-stu-id="ee531-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ee531-107">[in] Die Länge von `szName` als Anzahl von Zeichen. </span><span class="sxs-lookup"><span data-stu-id="ee531-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ee531-108">[out] Ein Zeiger auf die Gesamtzeichenanzahl des Assemblynamens.</span><span class="sxs-lookup"><span data-stu-id="ee531-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ee531-109">[out] Ein vom Aufrufer bereitgestellter Breitzeichenpuffer.</span><span class="sxs-lookup"><span data-stu-id="ee531-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="ee531-110">Bei Rückgabe der Funktion enthält er den Namen der Assembly.</span><span class="sxs-lookup"><span data-stu-id="ee531-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="ee531-111">[out] Ein Zeiger auf die ID der Anwendungsdomäne, die die Assembly enthält.</span><span class="sxs-lookup"><span data-stu-id="ee531-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="ee531-112">[out] Ein Zeiger auf die ID des Manifestmoduls der Assembly.</span><span class="sxs-lookup"><span data-stu-id="ee531-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee531-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ee531-113">Remarks</span></span>  
 <span data-ttu-id="ee531-114">Nach der Methodenrückgabe müssen Sie überprüfen, ob der `szName`-Puffer groß genug war, um den vollständigen Namen der Assembly aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="ee531-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="ee531-115">Vergleichen Sie hierzu den Wert, auf den `pcchName` verweist, mit dem Wert des `cchName`-Parameters.</span><span class="sxs-lookup"><span data-stu-id="ee531-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ee531-116">Wenn `pcchName` auf einen Wert verweist, der größer als `cchName` ist, weisen Sie einen größeren `szName`-Puffer zu, aktualisieren Sie `cchName` mit der neuen Größe, und rufen Sie `GetAssemblyInfo` erneut auf.</span><span class="sxs-lookup"><span data-stu-id="ee531-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="ee531-117">Alternativ können Sie zuerst `GetAssemblyInfo` mit einem `szName`-Puffer der Länge 0 (null) aufrufen, um die richtige Puffergröße zu ermitteln.</span><span class="sxs-lookup"><span data-stu-id="ee531-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ee531-118">Sie können die Puffergröße dann auf Basis des Werts anpassen, der von `pcchName` zurückgegeben wurde, und `GetAssemblyInfo` erneut aufrufen.</span><span class="sxs-lookup"><span data-stu-id="ee531-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee531-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ee531-119">Requirements</span></span>  
 <span data-ttu-id="ee531-120">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee531-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee531-121">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ee531-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ee531-122">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee531-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee531-123">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee531-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee531-124">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ee531-124">See Also</span></span>  
 [<span data-ttu-id="ee531-125">ICorProfilerInfo-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ee531-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="ee531-126">Profilerstellungsschnittstellen</span><span class="sxs-lookup"><span data-stu-id="ee531-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="ee531-127">Profilerstellung</span><span class="sxs-lookup"><span data-stu-id="ee531-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)