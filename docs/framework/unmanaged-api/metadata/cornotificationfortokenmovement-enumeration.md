---
title: CorNotificationForTokenMovement-Enumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNotificationForTokenMovement
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNotificationForTokenMovement
helpviewer_keywords: CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60d6c56394952fca84b45ba042f7d45a1dec6b1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement-Enumeration
Gibt an, die Benachrichtigungen, die an den Metadaten-API-Client gesendet werden, wenn ein token neuzuordnung auftritt.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`MDNotifyDefault`|Benachrichtigen, wenn `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, oder `mdFieldDef` Token verschieben.|  
|`MDNotifyAll`|Benachrichtigen Sie, wenn ein beliebiges Token verschoben wird.|  
|`MDNotifyNone`|Nicht benachrichtigen Sie, wenn Token verschieben.|  
|`MDNotifyMethodDef`|Benachrichtigen, wenn ein `mdMethodDef` -Token verschoben wird.|  
|`MDNotifyMemberRef`|Benachrichtigen, wenn ein `mdMemberRef` -Token verschoben wird.|  
|`MDNotifyFieldDef`|Benachrichtigen, wenn ein `mdFieldDef` -Token verschoben wird.|  
|`MDNotifyTypeRef`|Benachrichtigen, wenn ein `mdTypeRef` -Token verschoben wird.|  
|`MDNotifyTypeDef`|Benachrichtigen, wenn ein `mdTypeDef` -Token verschoben wird.|  
|`MDNotifyParamDef`|Benachrichtigen, wenn ein `mdParamDef` -Token verschoben wird.|  
|`MDNotifyInterfaceImpl`|Benachrichtigen, wenn ein `mdInterfaceImpl` -Token verschoben wird.|  
|`MDNotifyProperty`|Benachrichtigen, wenn ein `mdProperty` -Token verschoben wird.|  
|`MDNotifyEvent`|Benachrichtigen, wenn ein `mdEvent` -Token verschoben wird.|  
|`MDNotifySignature`|Benachrichtigen, wenn ein `mdSignature` -Token verschoben wird.|  
|`MDNotifyTypeSpec`|Benachrichtigen, wenn ein `mdTypeSpec` -Token verschoben wird.|  
|`MDNotifyCustomAttribute`|Benachrichtigen, wenn ein `mdCustomAttribute` -Token verschoben wird.|  
|`MDNotifySecurityValue`|Benachrichtigen, wenn ein `mdSecurityValue` -Token verschoben wird.|  
|`MDNotifyPermission`|Benachrichtigen, wenn ein `mdPermission` -Token verschoben wird.|  
|`MDNotifyModuleRef`|Benachrichtigen, wenn ein `mdModuleRef` -Token verschoben wird.|  
|`MDNotifyNameSpace`|Benachrichtigen, wenn ein `mdNameSpace` -Token verschoben wird.|  
|`MDNotifyAssemblyRef`|Benachrichtigen, wenn ein `mdAssemblyRef` -Token verschoben wird.|  
|`MDNotifyFile`|Benachrichtigen, wenn ein `mdFile` -Token verschoben wird.|  
|`MDNotifyExportedType`|Benachrichtigen, wenn ein `mdExportedType` -Token verschoben wird.|  
|`MDNotifyResource`|Benachrichtigen, wenn ein `mdManifestResource` -Token verschoben wird.|  
  
## <a name="remarks"></a>Hinweise  
 Ein Token möglicherweise erneut zugeordnet werden (die verschoben) beim Zusammenführen von Metadaten.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Metadatenenumerationen](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
