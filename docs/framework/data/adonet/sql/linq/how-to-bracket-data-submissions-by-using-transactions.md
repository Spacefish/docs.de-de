---
title: "Gewusst wie: Einklammern von Datenübergaben durch das Verwenden von Transaktionen"
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
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 071c0c8bc7e0bb8dca01e9fc51c66fb930ed102b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Gewusst wie: Einklammern von Datenübergaben durch das Verwenden von Transaktionen
Sie können <xref:System.Transactions.TransactionScope> verwenden, um die Übergaben zur Datenbank einzuklammern. Weitere Informationen finden Sie unter [Transaktionsunterstützung](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die Datenbankübergabe in einem <xref:System.Transactions.TransactionScope> eingeschlossen.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Siehe auch  
 [Downloading Sample Databases (Herunterladen von Beispieldatenbanken)](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Vornehmen und übergeben von Datenänderungen](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Transaktionsunterstützung](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)
