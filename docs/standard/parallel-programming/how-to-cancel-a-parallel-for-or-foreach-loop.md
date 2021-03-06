---
title: 'Gewusst wie: Abbrechen einer Parallel.For-Schleife oder einer ForEach-Schleife'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f82c5758e02b4beebf035fe8f43f856447855a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Gewusst wie: Abbrechen einer Parallel.For-Schleife oder einer ForEach-Schleife
Die <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> und <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Methoden unterstützen einen Abbruch durch die Verwendung von Abbruchtoken. Weitere Informationen über Abbrüche in der Regel finden Sie unter [Abbruch](../../../docs/standard/threading/cancellation-in-managed-threads.md). Geben Sie in einer parallelen Schleife die <xref:System.Threading.CancellationToken> an die Methode in der <xref:System.Threading.Tasks.ParallelOptions> Parameter und schließen Sie den parallelen Aufruf in einem Try / Catch-Block.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie einen Aufruf zum Abbrechen <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Sie können den gleichen Ansatz zum Anwenden einer <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> aufrufen.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Wenn das Token, das den Abbruch signalisiert dem token im angegeben sind die <xref:System.Threading.Tasks.ParallelOptions> -Instanz erfolgt, die parallele Schleife ein einzelnes auslöst, <xref:System.OperationCanceledException> einem Abbruch. Wenn ein anderes Token einen Abbruch verursacht, löst die Schleife ein <xref:System.AggregateException> mit einem <xref:System.OperationCanceledException> als ein "InnerException".  
  
## <a name="see-also"></a>Siehe auch  
 [Datenparallelität](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Lambdaausdrücke in PLINQ und TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
