---
title: SaveToHistory-Funktion (WPF nicht verwaltete API-Referenz)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: SaveToHistory
api_location: PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b30884433f81aa5e4bf1241ae4fe34494bef788e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="5bf9f-102">SaveToHistory-Funktion (WPF nicht verwaltete API-Referenz)</span><span class="sxs-lookup"><span data-stu-id="5bf9f-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="5bf9f-103">Diese API unterstützt die Windows Presentation Foundation (WPF)-Infrastruktur und sollte nicht direkt aus Ihrem Code verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5bf9f-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="5bf9f-104">Von der Windows Presentation Foundation (WPF)-Infrastruktur verwendet, für die Verwaltung von Windows.</span><span class="sxs-lookup"><span data-stu-id="5bf9f-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bf9f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5bf9f-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5bf9f-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="5bf9f-106">Parameters</span></span>  
 <span data-ttu-id="5bf9f-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="5bf9f-107">pHistoryStream</span></span>  
 <span data-ttu-id="5bf9f-108">Ein Zeiger auf den Verlauf Stream.</span><span class="sxs-lookup"><span data-stu-id="5bf9f-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bf9f-109">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5bf9f-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bf9f-110">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5bf9f-110">Requirements</span></span>  
 <span data-ttu-id="5bf9f-111">**Plattformen:** finden Sie unter [Systemanforderungen für .NET Framework](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bf9f-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bf9f-112">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="5bf9f-112">**DLL:**</span></span>  
  
 <span data-ttu-id="5bf9f-113">In .NET Framework 3.0 und 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="5bf9f-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="5bf9f-114">In .NET Framework 4 und höher: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="5bf9f-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="5bf9f-115">**.NET Framework-Version:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bf9f-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf9f-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5bf9f-116">See Also</span></span>  
 [<span data-ttu-id="5bf9f-117">WPF – Referenz zur nicht verwalteten API</span><span class="sxs-lookup"><span data-stu-id="5bf9f-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)