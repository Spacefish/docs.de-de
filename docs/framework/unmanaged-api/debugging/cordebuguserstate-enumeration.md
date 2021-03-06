---
title: CorDebugUserState-Enumeration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUserState
helpviewer_keywords: CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 95240dfea92a4ebbf2c7b9c11b7376d912c40fe5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState-Enumeration
Gibt den Benutzerzustand eines Threads an.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>Member  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|Beenden des Threads wurde angefordert.|  
|`USER_SUSPEND_REQUESTED`|Eine Unterbrechung des Threads wurde angefordert.|  
|`USER_BACKGROUND`|Der Thread wird im Hintergrund ausgeführt.|  
|`USER_UNSTARTED`|Der Thread wurde nicht gestartet, ausgeführt.|  
|`USER_STOPPED`|Der Thread wurde beendet.|  
|`USER_WAIT_SLEEP_JOIN`|Der Thread wartet darauf, dass ein anderer Thread eine Aufgabe auszuführen.|  
|`USER_SUSPENDED`|Der Thread wurde angehalten.|  
|`USER_UNSAFE_POINT`|Der Thread ist an einem unsicheren Punkt. Also der Thread an einem Punkt in der Ausführung, in denen es möglicherweise Garbagecollection verhindert.<br /><br /> Debuggen von Ereignissen können von unsicheren Punkten weitergeleitet werden, aber das Anhalten eines Threads an einem unsicheren Punkt wird sehr wahrscheinlich einen Deadlock bis der Thread fortgesetzt wird. Die sicheren und unsicheren Punkte werden durch den Just-in-Time (JIT) und die Garbage Collection Implementierung bestimmt.|  
|`USER_THREADPOOL`|Der Thread wird aus dem Threadpool.|  
  
## <a name="remarks"></a>Hinweise  
 Der Benutzerzustand eines Threads ist der Zustand, den der Thread hat, wenn der Debugger untersucht. Ein Thread möglicherweise eine Kombination des Benutzerstatus.  
  
 Verwenden der [ICorDebugThread:: GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) Methode, um Benutzerzustand eines Threads abzurufen.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Enumerationen](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
