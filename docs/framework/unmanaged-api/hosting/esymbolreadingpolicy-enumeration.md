---
title: ESymbolReadingPolicy-Enumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ESymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ESymbolReadingPolicy
helpviewer_keywords: ESymbolReadingPolicy enumeration [.NET Framework hosting]
ms.assetid: 4dc6c80d-b694-480b-a378-d5b18420ce17
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ce56486453e88a18ebd9dbb42f30bcfdafcf328e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="esymbolreadingpolicy-enumeration"></a>ESymbolReadingPolicy-Enumeration
Enthält Werte, die die Richtlinie für das Lesen der Programmdatenbankdateien (PDB) festgelegt.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum {  
    eSymbolReadingNever,  
    eSymbolReadingAlways,  
    eSymbolReadingFullTrustOnly  
} ESymbolReadingPolicy;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`eSymbolReadingAlways`|Gibt an, dass der Debugger immer PDB-Dateien lesen sollten.|  
|`eSymbolReadingFullTrustOnly`|Gibt an, dass der Debugger nur PDB-Dateien gelesen werden soll, die vollständig vertrauenswürdige Assemblys zugeordnet sind.|  
|`eSymbolReadingNever`|Gibt an, dass der Debugger niemals PDB-Dateien lesen soll.|  
  
## <a name="remarks"></a>Hinweise  
 Die `ESymbolReadingPolicy` Enumeration wird zusammen mit den [ICLRDebugManager:: SetSymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md) Methode.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** MSCorEE.h  
  
 **Bibliothek:** "Mscoree.dll"  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Hosten von Enumerationen](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
