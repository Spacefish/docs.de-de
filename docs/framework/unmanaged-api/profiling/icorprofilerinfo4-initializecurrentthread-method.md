---
title: ICorProfilerInfo4::InitializeCurrentThread-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc19ae86c266c74097bd649aa96f532528df3d7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread-Methode
Initialisiert den aktuellen Thread im Vorfeld nachfolgende Profiler, die auf dem gleichen Thread-API-Aufrufe, sodass dieser Deadlock vermieden werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Hinweise  
 Es wird empfohlen, Sie rufen `InitializeCurrentThread` auf einen beliebigen Thread, der einen Profiler angerufen API sind Threads angehalten. Diese Methode wird von Profilern, die ihre eigenen Thread aufrufen, erstellen in der Regel verwendet die [ICorProfilerInfo2:: DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) Methode zum Ausführen der Stapel durchläuft, während der Zielthread angehalten ist. Durch Aufrufen von `InitializeCurrentThread` Sobald bei der Profiler zuerst die Stichproben-Thread erstellt, können Profilern sicherstellen die pro Thread verzögerte Initialisierung, die die CLR beim ersten Aufruf andernfalls ausführen würden `DoStackSnapshot` kann nun erfolgen sicher Wenn keine anderen Threads sind angehalten.  
  
> [!NOTE]
>  `InitializeCurrentThread`führt die Initialisierung im voraus, um Aufgaben abgeschlossen sind, die Sperren und kann zu einem deadlock. Rufen Sie `InitializeCurrentThread` nur, wenn keine angehaltenen Threads vorhanden sind.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch  
 [ICorProfilerInfo4-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profilerstellungsschnittstellen](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilerstellung](../../../../docs/framework/unmanaged-api/profiling/index.md)
