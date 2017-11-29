---
title: ICorDebugFunction Schnittstelle1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction
helpviewer_keywords: ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 327ef9f74e94e3b1b20e78eb6a833038b5bfe16d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunction-interface1"></a><span data-ttu-id="61b6f-102">ICorDebugFunction Schnittstelle1</span><span class="sxs-lookup"><span data-stu-id="61b6f-102">ICorDebugFunction Interface1</span></span>
<span data-ttu-id="61b6f-103">Stellt eine verwaltete Funktion oder Methode dar.</span><span class="sxs-lookup"><span data-stu-id="61b6f-103">Represents a managed function or method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61b6f-104">Methoden</span><span class="sxs-lookup"><span data-stu-id="61b6f-104">Methods</span></span>  
  
|<span data-ttu-id="61b6f-105">Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-105">Method</span></span>|<span data-ttu-id="61b6f-106">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="61b6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61b6f-107">CreateBreakpoint-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|<span data-ttu-id="61b6f-108">Erstellt einen Haltepunkt am Anfang dieser Funktion.</span><span class="sxs-lookup"><span data-stu-id="61b6f-108">Creates a breakpoint at the beginning of this function.</span></span>|  
|[<span data-ttu-id="61b6f-109">GetClass-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-109">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|<span data-ttu-id="61b6f-110">Ruft ein ICorDebugClass-Objekt, das die Klasse darstellt, der diese Funktion ein Mitglied ist.</span><span class="sxs-lookup"><span data-stu-id="61b6f-110">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>|  
|[<span data-ttu-id="61b6f-111">GetCurrentVersionNumber-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-111">GetCurrentVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|<span data-ttu-id="61b6f-112">Ruft die Versionsnummer der letzten Änderung dieser Funktion ab.</span><span class="sxs-lookup"><span data-stu-id="61b6f-112">Gets the version number of the latest edit made to this function.</span></span>|  
|[<span data-ttu-id="61b6f-113">GetILCode-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-113">GetILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|<span data-ttu-id="61b6f-114">Ruft die Microsoft intermediate Language (MSIL)-Code für diese Funktion.</span><span class="sxs-lookup"><span data-stu-id="61b6f-114">Gets the Microsoft intermediate language (MSIL) code for this function.</span></span>|  
|[<span data-ttu-id="61b6f-115">GetLocalVarSigToken-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-115">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|<span data-ttu-id="61b6f-116">Ruft das Metadatentoken für die Signatur der lokalen Variablen der Funktion, die von diesem dargestellt wird `ICorDebugFunction` Instanz.</span><span class="sxs-lookup"><span data-stu-id="61b6f-116">Gets the metadata token for the local variable signature of the function that is represented by this `ICorDebugFunction` instance.</span></span>|  
|[<span data-ttu-id="61b6f-117">GetModule-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-117">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="61b6f-118">Ruft das Modul, in dem diese Funktion definiert ist.</span><span class="sxs-lookup"><span data-stu-id="61b6f-118">Gets the module in which this function is defined.</span></span>|  
|[<span data-ttu-id="61b6f-119">GetNativeCode-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-119">GetNativeCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|<span data-ttu-id="61b6f-120">Ruft den systemeigenen Code für diese Funktion.</span><span class="sxs-lookup"><span data-stu-id="61b6f-120">Gets the native code for this function.</span></span>|  
|[<span data-ttu-id="61b6f-121">GetToken-Methode</span><span class="sxs-lookup"><span data-stu-id="61b6f-121">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|<span data-ttu-id="61b6f-122">Ruft die Metadaten für diese Funktion ab.</span><span class="sxs-lookup"><span data-stu-id="61b6f-122">Gets the metadata token for this function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61b6f-123">Hinweise</span><span class="sxs-lookup"><span data-stu-id="61b6f-123">Remarks</span></span>  
 <span data-ttu-id="61b6f-124">Die `ICorDebugFunction` Schnittstelle stellt eine Funktion mit generischen Typparametern keine dar.</span><span class="sxs-lookup"><span data-stu-id="61b6f-124">The `ICorDebugFunction` interface does not represent a function with generic type parameters.</span></span> <span data-ttu-id="61b6f-125">Angenommen, ein `ICorDebugFunction` Instanz darstellen würde `Func<T>` , aber nicht `Func<string>`.</span><span class="sxs-lookup"><span data-stu-id="61b6f-125">For example, an `ICorDebugFunction` instance would represent `Func<T>` but not `Func<string>`.</span></span> <span data-ttu-id="61b6f-126">Rufen Sie [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) zum Abrufen der generischen Typparameter.</span><span class="sxs-lookup"><span data-stu-id="61b6f-126">Call [ICorDebugILFrame2::EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md) to get the generic type parameters.</span></span>  
  
 <span data-ttu-id="61b6f-127">Die Beziehung zwischen einer Methode Metadatentoken `mdMethodDef`, und eine Methode `ICorDebugFunction` Objekt ist abhängig von bearbeiten und Fortfahren ist, ob für die Funktion zulässig:</span><span class="sxs-lookup"><span data-stu-id="61b6f-127">The relationship between a method's metadata token, `mdMethodDef`, and a method's `ICorDebugFunction` object is dependent upon whether Edit and Continue is allowed on the function:</span></span>  
  
-   <span data-ttu-id="61b6f-128">Wenn Bearbeiten und Fortfahren wird für die Funktion nicht zulässig, besteht eine 1: 1-Beziehung zwischen der `ICorDebugFunction` Objekt und die `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="61b6f-128">If Edit and Continue is not allowed on the function, a one-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="61b6f-129">D. h. die Funktion verfügt über einen `ICorDebugFunction` -Objekt und ein `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="61b6f-129">That is, the function has one `ICorDebugFunction` object and one `mdMethodDef` token.</span></span>  
  
-   <span data-ttu-id="61b6f-130">Wenn Bearbeiten und Fortfahren für die Funktion zulässig ist, besteht eine viele-zu-eins-Beziehung zwischen der `ICorDebugFunction` Objekt und die `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="61b6f-130">If Edit and Continue is allowed on the function, a many-to-one relationship exists between the `ICorDebugFunction` object and the `mdMethodDef` token.</span></span> <span data-ttu-id="61b6f-131">D. h. möglicherweise die Funktion vielen Instanzen von `ICorDebugFunction`, eine für jede Version der Funktion, aber nur eine `mdMethodDef` token.</span><span class="sxs-lookup"><span data-stu-id="61b6f-131">That is, the function may have many instances of `ICorDebugFunction`, one for each version of the function, but only one `mdMethodDef` token.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61b6f-132">Diese Schnittstelle kann weder computerübergreifend noch prozessübergreifend remote aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="61b6f-132">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61b6f-133">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="61b6f-133">Requirements</span></span>  
 <span data-ttu-id="61b6f-134">**Plattformen:** finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61b6f-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61b6f-135">**Header:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61b6f-135">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61b6f-136">**Bibliothek:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61b6f-136">**Library:**  CorGuids.lib</span></span>  
  
 <span data-ttu-id="61b6f-137">**.NET Framework-Versionen:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61b6f-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b6f-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="61b6f-138">See Also</span></span>  
 [<span data-ttu-id="61b6f-139">Debugschnittstellen</span><span class="sxs-lookup"><span data-stu-id="61b6f-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)