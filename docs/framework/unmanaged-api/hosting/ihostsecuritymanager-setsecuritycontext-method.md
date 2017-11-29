---
title: IHostSecurityManager::SetSecurityContext-Methode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.SetSecurityContext
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::SetSecurityContext
helpviewer_keywords:
- SetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::SetSecurityContext method [.NET Framework hosting]
ms.assetid: e4372384-ee69-48d7-97e0-8fab7866597a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c25b8bb0effb4e5e1e61447c74c9729989d04702
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanagersetsecuritycontext-method"></a><span data-ttu-id="ce97c-102">IHostSecurityManager::SetSecurityContext-Methode</span><span class="sxs-lookup"><span data-stu-id="ce97c-102">IHostSecurityManager::SetSecurityContext Method</span></span>
<span data-ttu-id="ce97c-103">Legt den Sicherheitskontext des aktuell ausgeführten Threads fest.</span><span class="sxs-lookup"><span data-stu-id="ce97c-103">Sets the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce97c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce97c-104">Syntax</span></span>  
  
```  
HRESULT SetSecurityContext (  
    [in]  EContextType eContextType,  
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce97c-105">Parameter</span><span class="sxs-lookup"><span data-stu-id="ce97c-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="ce97c-106">[in] Eines der [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) Werte, der angibt, welche Art von Kontext die common Language Runtime (CLR) auf dem Host platziert wird.</span><span class="sxs-lookup"><span data-stu-id="ce97c-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of context the common language runtime (CLR) is placing on the host.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="ce97c-107">[out] Ein Zeiger auf die Adresse eines neuen [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) Objekt.</span><span class="sxs-lookup"><span data-stu-id="ce97c-107">[out] A pointer to the address of a new [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce97c-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ce97c-108">Return Value</span></span>  
  
|<span data-ttu-id="ce97c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ce97c-109">HRESULT</span></span>|<span data-ttu-id="ce97c-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ce97c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ce97c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ce97c-111">S_OK</span></span>|<span data-ttu-id="ce97c-112">`SetSecurityContext`wurde erfolgreich zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="ce97c-112">`SetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="ce97c-113">HOST_E_CLRNOTAVAILABLE ZURÜCK</span><span class="sxs-lookup"><span data-stu-id="ce97c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ce97c-114">Die CLR wurde nicht in einen Prozess geladen, oder die CLR wird in einem Zustand, in dem er nicht verwalteten Code ausführen oder den Aufruf erfolgreich verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="ce97c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ce97c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ce97c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ce97c-116">Der Aufruf ist ein Timeout aufgetreten.</span><span class="sxs-lookup"><span data-stu-id="ce97c-116">The call timed out.</span></span>|  
|<span data-ttu-id="ce97c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ce97c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ce97c-118">Der Aufrufer ist nicht Besitzer der Sperre.</span><span class="sxs-lookup"><span data-stu-id="ce97c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ce97c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ce97c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ce97c-120">Ein Ereignis wurde abgebrochen, während ein blockierten Thread oder eine Fiber darauf gewartet.</span><span class="sxs-lookup"><span data-stu-id="ce97c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ce97c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ce97c-121">E_FAIL</span></span>|<span data-ttu-id="ce97c-122">Ein Unbekannter Schwerwiegender Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="ce97c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ce97c-123">Wenn eine Methode E_FAIL zurückgibt, ist die CLR nicht mehr verwendbar innerhalb des Prozesses.</span><span class="sxs-lookup"><span data-stu-id="ce97c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ce97c-124">Nachfolgende Aufrufe zum Hosten der Methoden HOST_E_CLRNOTAVAILABLE zurück.</span><span class="sxs-lookup"><span data-stu-id="ce97c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce97c-125">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ce97c-125">Remarks</span></span>  
 <span data-ttu-id="ce97c-126">Die CLR ruft `SetSecurityContext` in verschiedenen Szenarien.</span><span class="sxs-lookup"><span data-stu-id="ce97c-126">The CLR calls `SetSecurityContext` in several scenarios.</span></span> <span data-ttu-id="ce97c-127">Bevor sie Module Konstruktoren und Klassen und Finalizer ausgeführt wird, ruft die CLR `SetSecurityContext` an den Host von Ausführungsfehlern zu schützen.</span><span class="sxs-lookup"><span data-stu-id="ce97c-127">Before it executes class and module constructors and finalizers, the CLR calls `SetSecurityContext` to protect the host from execution failures.</span></span> <span data-ttu-id="ce97c-128">Klicken Sie dann zurückgesetzt Sicherheitskontext auf den ursprünglichen Zustand nach der Ausführung der Konstruktor oder die Finalize-Methode mit einem weiteren Aufruf von `SetSecurityContext`.</span><span class="sxs-lookup"><span data-stu-id="ce97c-128">It then resets the security context to its original state after execution of the constructor or finalizer, by using another call to `SetSecurityContext`.</span></span> <span data-ttu-id="ce97c-129">Ein ähnlichen Muster tritt bei e/a-Abschluss.</span><span class="sxs-lookup"><span data-stu-id="ce97c-129">A similar pattern occurs with I/O completion.</span></span> <span data-ttu-id="ce97c-130">Wenn der Host implementiert [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), die CLR ruft `SetSecurityContext` nach der Host ruft [ICLRIoCompletionManager:: OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span><span class="sxs-lookup"><span data-stu-id="ce97c-130">If the host implements [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md), the CLR calls `SetSecurityContext` after the host calls [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
 <span data-ttu-id="ce97c-131">An asynchronen Punkten in Arbeitsthreads, die CLR ruft `SetSecurityContext` in <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> oder innerhalb [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), je nachdem, ob der Host oder die CLR den Threadpool implementiert.</span><span class="sxs-lookup"><span data-stu-id="ce97c-131">At asynchronous points in worker threads, the CLR calls `SetSecurityContext` within <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> or within [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md), depending on whether the host or the CLR is implementing the thread pool.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce97c-132">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ce97c-132">Requirements</span></span>  
 <span data-ttu-id="ce97c-133">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce97c-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce97c-134">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce97c-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce97c-135">**Bibliothek:** als Ressource in MSCorEE.dll enthalten</span><span class="sxs-lookup"><span data-stu-id="ce97c-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce97c-136">**.NET Framework-Versionen:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce97c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce97c-137">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ce97c-137">See Also</span></span>  
 <xref:System.Threading.ThreadPool?displayProperty=nameWithType>  
 [<span data-ttu-id="ce97c-138">EContextType-Enumeration</span><span class="sxs-lookup"><span data-stu-id="ce97c-138">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)  
 [<span data-ttu-id="ce97c-139">ICLRIoCompletionManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ce97c-139">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="ce97c-140">IHostIoCompletionManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ce97c-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="ce97c-141">IHostSecurityContext-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ce97c-141">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="ce97c-142">IHostSecurityManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ce97c-142">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="ce97c-143">IHostThreadPoolManager-Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="ce97c-143">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)