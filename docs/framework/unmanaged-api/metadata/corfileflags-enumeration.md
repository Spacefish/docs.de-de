---
title: CorFileFlags-Enumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileFlags
helpviewer_keywords: CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf123f734f73ecfe726a80099de6ec06b0ced06b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="44468-102">CorFileFlags-Enumeration</span><span class="sxs-lookup"><span data-stu-id="44468-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="44468-103">Enthält Werte, die den Typ der Datei, die in einem Aufruf definiert beschreiben [IMetaDataAssemblyEmit:: DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="44468-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44468-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="44468-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="44468-105">Member</span><span class="sxs-lookup"><span data-stu-id="44468-105">Members</span></span>  
  
|<span data-ttu-id="44468-106">Member</span><span class="sxs-lookup"><span data-stu-id="44468-106">Member</span></span>|<span data-ttu-id="44468-107">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="44468-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="44468-108">Gibt an, dass die Datei nicht mit einer Ressourcendatei gespeichert ist.</span><span class="sxs-lookup"><span data-stu-id="44468-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="44468-109">Gibt an, dass die Datei, die möglicherweise eine Ressourcendatei keine Metadaten enthält.</span><span class="sxs-lookup"><span data-stu-id="44468-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="44468-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="44468-110">Requirements</span></span>  
 <span data-ttu-id="44468-111">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44468-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44468-112">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="44468-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="44468-113">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44468-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44468-114">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="44468-114">See Also</span></span>  
 [<span data-ttu-id="44468-115">Metadatenenumerationen</span><span class="sxs-lookup"><span data-stu-id="44468-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)