---
title: StrongNameGetBlob-Funktion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a88131e4a764c963d24a698935ebb12e0daa96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="30558-102">StrongNameGetBlob-Funktion</span><span class="sxs-lookup"><span data-stu-id="30558-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="30558-103">Füllt den angegebenen Puffer mit der binären Darstellung der ausführbaren Datei an der angegebenen Adresse an.</span><span class="sxs-lookup"><span data-stu-id="30558-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="30558-104">Diese Funktion ist veraltet.</span><span class="sxs-lookup"><span data-stu-id="30558-104">This function has been deprecated.</span></span> <span data-ttu-id="30558-105">Verwenden der [ICLRStrongName:: StrongNameGetBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) Methode stattdessen.</span><span class="sxs-lookup"><span data-stu-id="30558-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30558-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="30558-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30558-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="30558-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="30558-108">[in] Einen gültigen Pfad zur ausführbaren Datei geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="30558-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="30558-109">[in] Der Puffer, in dem die ausführbare Datei geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="30558-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="30558-110">[in, out] Die maximale Größe in Bytes, des angeforderten `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="30558-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="30558-111">Nach der Rückgabe der tatsächlichen Größe in Bytes, der `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="30558-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30558-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="30558-112">Return Value</span></span>  
 <span data-ttu-id="30558-113">`true`Bei erfolgreichem Abschluss; andernfalls `false`.</span><span class="sxs-lookup"><span data-stu-id="30558-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30558-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="30558-114">Remarks</span></span>  
 <span data-ttu-id="30558-115">Wenn die `StrongNameGetBlob` Funktion nicht erfolgreich abgeschlossen wird, rufen Sie die [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) Funktion, um den letzten generierten Fehler abzurufen.</span><span class="sxs-lookup"><span data-stu-id="30558-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30558-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="30558-116">Requirements</span></span>  
 <span data-ttu-id="30558-117">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30558-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30558-118">**Header:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="30558-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="30558-119">**Bibliothek:** als Ressource in MsCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="30558-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30558-120">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30558-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30558-121">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="30558-121">See Also</span></span>  
 [<span data-ttu-id="30558-122">StrongNameGetBlob-Methode</span><span class="sxs-lookup"><span data-stu-id="30558-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="30558-123">StrongNameGetBlobFromImage-Methode</span><span class="sxs-lookup"><span data-stu-id="30558-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="30558-124">ICLRStrongName-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="30558-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)