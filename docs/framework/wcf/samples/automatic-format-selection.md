---
title: Automatische Formatauswahl
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dab51e56-8517-4a6a-bb54-b55b15ab37bb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92934e9e9e8cbd38a7f00b1c7846d3e1b8dba583
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2017
---
# <a name="automatic-format-selection"></a>Automatische Formatauswahl
In diesem Beispiel wird veranschaulicht, wie die automatische Formatauswahl (XML oder JSON) mit dem [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]-Web-REST-Programmiermodell aktiviert wird und wie das Format im Vorgangscode explizit festgelegt wird.  
  
## <a name="sample-details"></a>Beispieldetails  
 Das Beispiel besteht aus einem Dienst und Clientcode, mit dem Anforderungen an den Dienst gesendet werden. Der Dienst unterstützt einen einzelnen HTTP-`GET`-Vorgang (`EchoWithGet`) und einen einzelnen HTTP-`POST`-Vorgang (`EchoWithPost`). Bei beiden Vorgängen wird eine Zeichenfolge erwartet, die als Antwort wieder zurückgegeben wird. Der Zeichenfolge wird mithilfe des `GET`-Vorgangs in einem URI-Abfragezeichenfolgenparameter bereitgestellt. Der Zeichenfolge wird mit dem `POST`-Vorgang im Text der Anforderung bereitgestellt und in XML serialisiert. Der Dienst kann Antworten in XML oder JSON zurückgeben. Dazu werden die neue automatische Formatauswahl und die imperativen Formatauswahlfunktionen in [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] verwendet.  
  
 In diesem Beispiel wird die automatische Formatauswahl mit der Datei App.config aktiviert. Im standardmäßigen HTTP-Webendpunkt wurde dem `automaticFormatSelectionEnabled`-Attribut der Wert `true` zugewiesen. Da die automatische Formatauswahl aktiviert ist, wählt die [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Infrastruktur das Antwortformat (XML oder JSON) aus, das aufgrund der HTTP Accept- oder Content-Type-Header der Anforderung am geeignetsten scheint. Der Entwickler muss keinen zusätzlichen Code und keine zusätzliche Konfiguration bereitstellen, sondern nur das `automaticFormatSelectionEnabled`-Attribut auf `true` festlegen, um diese neue Funktion zu verwenden. Im Clientcode in "Program.cs", Anforderungen gesendet werden sowohl die `GET` und `POST` Vorgänge des Diensts mit dem HTTP-Accept-Header, die als "Application/Xml" oder "Application/Json" angegeben und der Dienst gibt eine Antwort zurück, in diesem jeweiligen Format.  
  
 Beim `GET`-Vorgang wird außerdem die imperative Formatauswahl verwendet. Der `GET`-Vorgang überprüft, ob es einen optionalen `format`-Abfragezeichenfolgenparameter gibt und legt das Antwortformat für die <xref:System.ServiceModel.Web.WebOperationContext.OutgoingResponse%2A>-Eigenschaft fest, falls ein entsprechender Parameter vorhanden ist. Durch das imperative Festlegen des Antwortformats in der beschriebenen Weise wird die von der [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-Infrastruktur vorgenommene automatische Formatauswahl überschrieben.  
  
 Das Beispiel umfasst einen selbst gehosteten Dienst und einen Client, der in einer Konsolenanwendung ausgeführt wird. Während die Konsolenanwendung ausgeführt wird, sendet der Client Anforderungen an den Dienst und schreibt die in den Antworten enthaltenen wichtigen Informationen in das Konsolenfenster.  
  
#### <a name="to-use-this-sample"></a>So verwenden Sie dieses Beispiel  
  
1.  Öffnen Sie die Projektmappe für das Beispiel zur automatischen Formatauswahl. Sie müssen [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] als Administrator ausführen, damit das Beispiel erfolgreich ausgeführt werden kann. Zu diesem Zweck mit der rechten Maustaste die [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Symbol, und wählen Sie **als Administrator ausführen** aus dem Kontextmenü.  
  
2.  Drücken Sie STRG+UMSCHALT+B, um die Projektmappe zu erstellen, und dann STRG+F5, um das Projekt AutomaticFormatSelection der Konsolenanwendung auszuführen. Im eingeblendeten Konsolenfenster werden der URI des ausgeführten Diensts und der URI der HTML-Hilfeseite für den ausgeführten Dienst angezeigt.  
  
3.  Während das Beispiel ausgeführt wird, sendet der Client Anforderungen an den Dienst und schreibt die Antworten in das Konsolenfenster. Beachten Sie die anderen Formate der Antworten in XML und JSON.  
  
4.  Drücken Sie eine beliebige Taste, um das Beispiel zu beenden.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AutomaticFormatSelection`  
  
## <a name="see-also"></a>Siehe auch
