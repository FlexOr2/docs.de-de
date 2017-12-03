---
title: IMetaDataImport::FindMethod-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMethod
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b081a5e3668110ea6281c245f507b56ac48b9ab5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="31355-102">IMetaDataImport::FindMethod-Methode</span><span class="sxs-lookup"><span data-stu-id="31355-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="31355-103">Ruft einen Zeiger auf das MethodDef token für die Methode, die eingeschlossen ist durch das angegebene <xref:System.Type> und den angegebenen Namen und Metadaten aufweist.</span><span class="sxs-lookup"><span data-stu-id="31355-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31355-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="31355-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31355-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="31355-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="31355-106">[in] Die `mdTypeDef` token für den Typ (eine Klasse oder Schnittstelle), das der gesuchten Member enthält.</span><span class="sxs-lookup"><span data-stu-id="31355-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="31355-107">Wenn dieser Wert ist `mdTokenNil`, und klicken Sie dann die Suche für eine globale Funktion ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="31355-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="31355-108">[in] Der Name der zu suchenden Methode.</span><span class="sxs-lookup"><span data-stu-id="31355-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="31355-109">[in] Ein Zeiger auf die binäre Metadatensignatur der Methode.</span><span class="sxs-lookup"><span data-stu-id="31355-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="31355-110">[in] Die Größe in Bytes des `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="31355-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="31355-111">[out] Ein Zeiger auf das übereinstimmende MethodDef-Token.</span><span class="sxs-lookup"><span data-stu-id="31355-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31355-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="31355-112">Remarks</span></span>  
 <span data-ttu-id="31355-113">Geben Sie die Methode, die mit der einschließenden Klasse oder Schnittstelle (`td`), seinen Namen (`szName`), und optional die Signatur (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="31355-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="31355-114">Es gibt möglicherweise mehrere Methoden mit demselben Namen in einer Klasse oder Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="31355-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="31355-115">Übergeben Sie in diesem Fall die Methodensignatur, um die eindeutige Übereinstimmung zu finden.</span><span class="sxs-lookup"><span data-stu-id="31355-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="31355-116">Die Signatur zu übergeben, um `FindMethod` muss wurden im aktuellen Bereich generiert wurde, da Signaturen an einen bestimmten Bereich gebunden sind.</span><span class="sxs-lookup"><span data-stu-id="31355-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="31355-117">Eine Signatur kann ein Token einbetten, die die einschließende Klasse oder der angegebene Werttyp identifiziert.</span><span class="sxs-lookup"><span data-stu-id="31355-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="31355-118">Das Token ist ein Index in die lokale TypeDef-Tabelle.</span><span class="sxs-lookup"><span data-stu-id="31355-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="31355-119">Sie erstellen eine Laufzeit-Signatur im Kontext des aktuellen Gültigkeitsbereichs und verwenden Sie diese Signatur als Eingabe können nicht `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="31355-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="31355-120">`FindMethod`Sucht nur Methoden, die direkt in der Klasse oder Schnittstelle definiert wurden. Es findet keine geerbte Methoden.</span><span class="sxs-lookup"><span data-stu-id="31355-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31355-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="31355-121">Requirements</span></span>  
 <span data-ttu-id="31355-122">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31355-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31355-123">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="31355-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31355-124">**Bibliothek:** als Ressource in MsCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="31355-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="31355-125">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31355-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31355-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="31355-126">See Also</span></span>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="31355-127">IMetaDataImport-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="31355-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="31355-128">IMetaDataImport2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="31355-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)