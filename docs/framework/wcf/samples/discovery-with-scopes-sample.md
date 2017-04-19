---
title: "Beispiel f&#252;r Suche mit Bereichen | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Beispiel f&#252;r Suche mit Bereichen
In diesem Beispiel wird veranschaulicht, wie Bereiche verwendet werden, um erkennbare Endpunkte zu kategorisieren, und wie <xref:System.ServiceModel.Discovery.DiscoveryClient> verwendet wird, um eine asynchrone Suche nach Endpunkten durchzuführen.In Bezug auf den Dienst wird in diesem Beispiel veranschaulicht, wie die Suche für jeden Endpunkt angepasst wird, indem ein Endpunktsuchverhalten hinzugefügt und damit ein Bereich zum Endpunkt hinzugefügt sowie die Ermittelbarkeit des Endpunkts gesteuert wird.In Bezug auf den Client wird in diesem Beispiel beschrieben, wie Clients einen <xref:System.ServiceModel.Discovery.DiscoveryClient> erstellen und die Suchparameter optimieren können, um Bereiche einzuschließen, indem Bereiche zu <xref:System.ServiceModel.Discovery.FindCriteria> hinzugefügt werden.In diesem Beispiel wird auch gezeigt, wie Clients Antworten durch Hinzufügen eines Beendigungskriteriums einschränken können.  
  
## Dienstfunktionen  
 In diesem Projekt wird gezeigt, wie zwei Dienstendpunkte zu einem <xref:System.ServiceModel.ServiceHost> hinzugefügt werden.Jedem Endpunkt ist ein <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> zugeordnet.Dieses Verhalten wird verwendet, um URI\-Bereiche für beide Endpunkte hinzuzufügen.Bereiche werden zur Unterscheidung der einzelnen Endpunkte verwendet, damit die Clients die Suche optimieren können.Für den zweiten Endpunkt kann die Ermittelbarkeit deaktiviert werden, indem die <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A>\-Eigenschaft auf `false` festgelegt wird.Dadurch wird sichergestellt, dass die diesem Endpunkt zugeordneten Suchmetadaten nicht als Teil der Suchnachrichten gesendet werden.  
  
## Clientfunktionen  
 Die `FindCalculatorServiceAddress()`\-Methode veranschaulicht die Verwendung von einem <xref:System.ServiceModel.Discovery.DiscoveryClient> und die Übergabe von <xref:System.ServiceModel.Discovery.FindCriteria> mit zwei Einschränkungen.Den Kriterien wird ein Bereich hinzugefügt, und die <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>\-Eigenschaft wird auf 1 festgelegt.Der Bereich beschränkt die Ergebnisse auf die Dienste, die den gleichen Bereich veröffentlichen.Durch Festlegen von <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> auf 1 werden die Antworten, auf die der <xref:System.ServiceModel.Discovery.DiscoveryClient> wartet, auf maximal einen Endpunkt beschränkt.Der <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>\-Aufruf ist ein synchroner Vorgang, der den Thread blockiert, bis ein Timeout überschritten bzw. ein Endpunkt gefunden wird.  
  
#### So verwenden Sie dieses Beispiel  
  
1.  In diesem Beispiel werden HTTP\-Endpunkte verwendet. Zur Ausführung des Beispiels müssen die richtigen URL\-ACLs hinzugefügt werden.Weitere Informationen finden Sie unter [Konfigurieren von HTTP und HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).Durch die Ausführung des folgenden Befehls mit erweiterten Berechtigungen werden die entsprechenden ACLs hinzugefügt.Es empfiehlt sich, die folgenden Argumente durch die Domäne und den Benutzernamen zu ersetzen, wenn der Befehl nicht funktioniert: `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  Erstellen Sie die Projektmappe.  
  
3.  Führen Sie die ausführbare Dienstdatei aus dem Buildverzeichnis aus.  
  
4.  Führen Sie die ausführbare Clientanwendung aus.Beachten Sie, dass der Client in der Lage ist, den Dienst zu finden.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert.Suchen Sie nach dem folgenden Verzeichnis \(Standardverzeichnis\), bevor Sie fortfahren.  
>   
>  `<Installationslaufwerk>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation \(WCF\) and Windows Workflow Foundation \(WF\) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]\- und [!INCLUDE[wf1](../../../../includes/wf1-md.md)]\-Beispiele herunterzuladen.Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`  
  
## Siehe auch