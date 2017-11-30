---
title: ICorDebugModule::GetMetaDataInterface-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetMetaDataInterface
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4b1944c68db0cbdd8eb49e10433defc953e4494
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="0857f-102">ICorDebugModule::GetMetaDataInterface-Methode</span><span class="sxs-lookup"><span data-stu-id="0857f-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="0857f-103">Ruft eine Metadaten-Schnittstellenobjekts, das verwendet werden kann, um die Metadaten für das Modul untersuchen.</span><span class="sxs-lookup"><span data-stu-id="0857f-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0857f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0857f-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0857f-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="0857f-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="0857f-106">[in] Die Verweis-ID, die die Metadatenschnittstelle angegeben.</span><span class="sxs-lookup"><span data-stu-id="0857f-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="0857f-107">[out] Ein Zeiger auf die Adresse des ein `T:IUnknown` Objekt, das eines der [Metadatenschnittstellen](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="0857f-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0857f-108">Hinweise</span><span class="sxs-lookup"><span data-stu-id="0857f-108">Remarks</span></span>  
 <span data-ttu-id="0857f-109">Der Debugger können Sie die `GetMetaDataInterface` Methode, um eine Kopie der ursprünglichen Metadaten für ein Modul erstellen.</span><span class="sxs-lookup"><span data-stu-id="0857f-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="0857f-110">Der Debugger ruft `GetMetaDataInterface` zum Abrufen einer [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) -Schnittstellenobjekt für das Modul ruft dann [IMetaDataEmit:: SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) um eine Kopie der Metadaten des Moduls in den Arbeitsspeicher zu speichern.</span><span class="sxs-lookup"><span data-stu-id="0857f-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0857f-111">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="0857f-111">Requirements</span></span>  
 <span data-ttu-id="0857f-112">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0857f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0857f-113">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0857f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0857f-114">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0857f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0857f-115">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0857f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0857f-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="0857f-116">See Also</span></span>  
 [<span data-ttu-id="0857f-117">Metadaten</span><span class="sxs-lookup"><span data-stu-id="0857f-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)