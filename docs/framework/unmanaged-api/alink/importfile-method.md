---
title: ImportFile-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile
helpviewer_keywords: ImportFile method
ms.assetid: bcbe321f-b83a-4e9a-9f10-8d913e244dc9
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46830699ba43c406da313653e1910e8f7a18a2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="importfile-method"></a><span data-ttu-id="bbfae-102">ImportFile-Methode</span><span class="sxs-lookup"><span data-stu-id="bbfae-102">ImportFile Method</span></span>
<span data-ttu-id="bbfae-103">Imports-Assemblys und ungebundenen Modulen.</span><span class="sxs-lookup"><span data-stu-id="bbfae-103">Imports assemblies and unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfae-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="bbfae-104">Syntax</span></span>  
  
```  
HRESULT ImportFile(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbfae-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="bbfae-105">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="bbfae-106">Vollständig qualifizierte Name des zu importierenden Datei.</span><span class="sxs-lookup"><span data-stu-id="bbfae-106">Fully qualified name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="bbfae-107">Optionale Ausgabedateiname, der verwendet werden kann, um die Datei zu benennen, wie sie in der Assembly verknüpft ist.</span><span class="sxs-lookup"><span data-stu-id="bbfae-107">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="bbfae-108">Bei "true", ImportTypes verwendet wird, andernfalls importieren muss manuell durchgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="bbfae-108">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="bbfae-109">Ein Zeiger auf das token, wo eine eindeutige Datei-ID gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="bbfae-109">Pointer to token where a unique file ID will be stored.</span></span> <span data-ttu-id="bbfae-110">Die Datei kann es sich um eine Assembly oder eine Datei sein.</span><span class="sxs-lookup"><span data-stu-id="bbfae-110">The file can be an assembly or a file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="bbfae-111">Zeiger auf empfängt [IMetaDataAssemblyImport-Schnittstelle](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span><span class="sxs-lookup"><span data-stu-id="bbfae-111">Receives pointer to [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md).</span></span> <span data-ttu-id="bbfae-112">NULL kann sein, wenn die Datei keine Assembly ist.</span><span class="sxs-lookup"><span data-stu-id="bbfae-112">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="bbfae-113">Ein Zeiger auf die Anzahl der Dateien und/oder Bereiche, die importiert wurden.</span><span class="sxs-lookup"><span data-stu-id="bbfae-113">Pointer to the count of files and/or scopes that have been imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbfae-114">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="bbfae-114">Return Value</span></span>  
 <span data-ttu-id="bbfae-115">Gibt S_OK zurück, wenn die Methode erfolgreich ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="bbfae-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfae-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="bbfae-116">Requirements</span></span>  
 <span data-ttu-id="bbfae-117">Erfordert alink.h</span><span class="sxs-lookup"><span data-stu-id="bbfae-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbfae-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bbfae-118">See Also</span></span>  
 [<span data-ttu-id="bbfae-119">IALink-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="bbfae-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="bbfae-120">IALink2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="bbfae-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="bbfae-121">ALink-API</span><span class="sxs-lookup"><span data-stu-id="bbfae-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)