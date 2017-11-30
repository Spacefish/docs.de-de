---
title: IAssemblyName::Finalize-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.Finalize
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::Finalize
helpviewer_keywords:
- Finalize method [.NET Framework fusion]
- IAssemblyName::Finalize method [.NET Framework fusion]
ms.assetid: 610e792d-98ef-411f-90b0-5b9a3813f547
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 137c9341dabeb6b7efd029cda5188fbc25308f1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblynamefinalize-method"></a><span data-ttu-id="e3f9c-102">IAssemblyName::Finalize-Methode</span><span class="sxs-lookup"><span data-stu-id="e3f9c-102">IAssemblyName::Finalize Method</span></span>
<span data-ttu-id="e3f9c-103">Dies ermöglicht [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) -Objekt, Ressourcen freizugeben und andere Bereinigungen durchzuführen, bevor der Destruktor aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="e3f9c-103">Allows this [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object to release resources and perform other cleanup operations before its destructor is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3f9c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3f9c-104">Syntax</span></span>  
  
```  
HRESULT Finalize ();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e3f9c-105">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e3f9c-105">Requirements</span></span>  
 <span data-ttu-id="e3f9c-106">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3f9c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3f9c-107">**Header:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e3f9c-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e3f9c-108">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3f9c-108">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f9c-109">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e3f9c-109">See Also</span></span>  
 [<span data-ttu-id="e3f9c-110">IAssemblyName-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="e3f9c-110">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)