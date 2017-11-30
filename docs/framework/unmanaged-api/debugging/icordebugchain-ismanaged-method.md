---
title: ICorDebugChain::IsManaged-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.IsManaged
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fe5736a1ca420eb361e062743ed93982e7ec3f29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="cea8e-102">ICorDebugChain::IsManaged-Methode</span><span class="sxs-lookup"><span data-stu-id="cea8e-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="cea8e-103">Ruft einen Wert, der angibt, ob diese Kette verwalteten Code ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="cea8e-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cea8e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="cea8e-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cea8e-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="cea8e-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="cea8e-106">[out] `true` Wenn diese Kette verwalteten Code ausgeführt wird, andernfalls `false`.</span><span class="sxs-lookup"><span data-stu-id="cea8e-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cea8e-107">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="cea8e-107">Requirements</span></span>  
 <span data-ttu-id="cea8e-108">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cea8e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cea8e-109">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cea8e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cea8e-110">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cea8e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cea8e-111">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cea8e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>