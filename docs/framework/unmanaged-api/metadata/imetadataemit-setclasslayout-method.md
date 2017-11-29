---
title: IMetaDataEmit::SetClassLayout-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetClassLayout
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetClassLayout
helpviewer_keywords:
- IMetaDataEmit::SetClassLayout method [.NET Framework metadata]
- SetClassLayout method [.NET Framework metadata]
ms.assetid: 2576c449-388d-4434-a0e1-9f53991e11b6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a68d94cbea408bee90b117965f83f760ba7ea5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetclasslayout-method"></a><span data-ttu-id="045cf-102">IMetaDataEmit::SetClassLayout-Methode</span><span class="sxs-lookup"><span data-stu-id="045cf-102">IMetaDataEmit::SetClassLayout Method</span></span>
<span data-ttu-id="045cf-103">Schließt das Layout der Felder für eine Klasse, die durch einen vorherigen Aufruf von definiert wurde [DefineTypeDef-Methode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="045cf-103">Completes the layout of fields for a class that has been defined by a prior call to [DefineTypeDef Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045cf-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="045cf-104">Syntax</span></span>  
  
```  
HRESULT SetClassLayout (  
    [in]  mdTypeDef           td,   
    [in]  DWORD               dwPackSize,   
    [in]  COR_FIELD_OFFSET    rFieldOffsets[],   
    [in]  ULONG               ulClassSize   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="045cf-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="045cf-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="045cf-106">[in] Ein `mdTypeDef` Token, das die Klasse angeordnet werden, angibt.</span><span class="sxs-lookup"><span data-stu-id="045cf-106">[in] An `mdTypeDef` token that specifies the class to be laid out.</span></span>  
  
 `dwPackSize`  
 <span data-ttu-id="045cf-107">[in] Die Komprimierungsgröße: 1, 2, 4, 8 oder 16 Bytes.</span><span class="sxs-lookup"><span data-stu-id="045cf-107">[in] The packing size: 1, 2, 4, 8 or 16 bytes.</span></span> <span data-ttu-id="045cf-108">Die Komprimierungsgröße ist die Anzahl von Bytes zwischen angrenzenden Felder.</span><span class="sxs-lookup"><span data-stu-id="045cf-108">The packing size is the number of bytes between adjacent fields.</span></span>  
  
 `rFieldOffsets`  
 <span data-ttu-id="045cf-109">[in] Ein Array von [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) Strukturen, von denen jede ein Feld der Klasse und das Feld den offset innerhalb der Klasse angibt.</span><span class="sxs-lookup"><span data-stu-id="045cf-109">[in] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which specifies a field of the class and the field's offset within the class.</span></span> <span data-ttu-id="045cf-110">Beenden Sie das Array mit `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="045cf-110">Terminate the array with `mdTokenNil`.</span></span>  
  
 `ulClassSize`  
 <span data-ttu-id="045cf-111">[in] Die Größe in Bytes, der-Klasse.</span><span class="sxs-lookup"><span data-stu-id="045cf-111">[in] The size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="045cf-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="045cf-112">Remarks</span></span>  
 <span data-ttu-id="045cf-113">Die Klasse definiert ist zunächst durch Aufrufen der [DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) -Methode und die Angabe eines der folgenden drei Layouts für die Felder der Klasse: automatisch, sequenziell oder explizit.</span><span class="sxs-lookup"><span data-stu-id="045cf-113">The class is initially defined by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method, and specifying one of three layouts for the fields of the class: automatic, sequential, or explicit.</span></span> <span data-ttu-id="045cf-114">Normalerweise verwenden Sie Automatisches Layout und die Common Language Runtime die beste Möglichkeit, um das Layout der Felder auswählen können.</span><span class="sxs-lookup"><span data-stu-id="045cf-114">Normally, you would use automatic layout and let the runtime choose the best way to lay out the fields.</span></span>  
  
 <span data-ttu-id="045cf-115">Allerdings sollten Sie die Felder angeordnet, gemäß der Anordnung, die nicht Code verwendet verwaltete.</span><span class="sxs-lookup"><span data-stu-id="045cf-115">However, you might want the fields laid out according to the arrangement that unmanaged code uses.</span></span> <span data-ttu-id="045cf-116">In diesem Fall wählen Sie entweder das sequenzielle oder explizite Layout und rufen `SetClassLayout` um das Layout der Felder abzuschließen:</span><span class="sxs-lookup"><span data-stu-id="045cf-116">In this case, choose either sequential or explicit layout and call `SetClassLayout` to complete the layout of the fields:</span></span>  
  
-   <span data-ttu-id="045cf-117">Sequenzielles Layout: Geben Sie die Komprimierungsgröße.</span><span class="sxs-lookup"><span data-stu-id="045cf-117">Sequential layout: Specify the packing size.</span></span> <span data-ttu-id="045cf-118">Ein Feld wird anhand seiner natürlichen Größe oder die Komprimierungsgröße, unabhängig davon, welche Ergebnisse in den kleineren Offset des Felds ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="045cf-118">A field is aligned according to either its natural size or the packing size, whichever results in the smaller offset of the field.</span></span> <span data-ttu-id="045cf-119">Legen Sie `rFieldOffsets` und `ulClassSize` auf 0 (null).</span><span class="sxs-lookup"><span data-stu-id="045cf-119">Set `rFieldOffsets` and `ulClassSize` to zero.</span></span>  
  
-   <span data-ttu-id="045cf-120">Explizites Layout: Geben Sie den Offset für jedes Feld, oder geben Sie die Klassengröße und die Komprimierungsgröße.</span><span class="sxs-lookup"><span data-stu-id="045cf-120">Explicit layout: Either specify the offset of each field or specify the class size and the packing size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="045cf-121">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="045cf-121">Requirements</span></span>  
 <span data-ttu-id="045cf-122">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="045cf-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="045cf-123">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="045cf-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="045cf-124">**Bibliothek:** als Ressource in MSCorEE.dll verwendet</span><span class="sxs-lookup"><span data-stu-id="045cf-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="045cf-125">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="045cf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045cf-126">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="045cf-126">See Also</span></span>  
 [<span data-ttu-id="045cf-127">IMetaDataEmit-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="045cf-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="045cf-128">IMetaDataEmit2-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="045cf-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)