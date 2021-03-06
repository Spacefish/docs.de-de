---
title: Entfernen von doppelten Elementen aus einer Sequenz
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 568b5e7553895c346f6a9de524ad6dd93117da43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Entfernen von doppelten Elementen aus einer Sequenz
Verwenden Sie den <xref:System.Linq.Queryable.Distinct%2A>-Operator, um doppelte Elemente aus einer Sequenz auszuschließen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird <xref:System.Linq.Queryable.Distinct%2A> verwendet, um eine Sequenz der eindeutigen Orte auszuwählen, die Kunden aufweisen.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Siehe auch  
 [Beispiele für Abfragen](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
