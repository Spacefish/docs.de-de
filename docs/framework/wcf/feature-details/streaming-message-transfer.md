---
title: "Nachrichten&#252;bertragung per Stream | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Nachrichten&#252;bertragung per Stream
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]\-Transporte unterstützen zwei Modi zum Übertragen von Nachrichten:  
  
-   Bei gepufferten Übertragungen wird die gesamte Nachricht in einem Puffer zwischengespeichert, bis die Übertragung abgeschlossen ist.Gepufferte Nachrichten müssen vollständig übertragen worden sein, bevor sie vom Empfänger gelesen werden können.  
  
-   Bei Streamingübertragungen wird die Nachricht als Stream verfügbar gemacht.Die Nachricht kann vom Empfänger verarbeitet werden, bevor sie vollständig empfangen wurde.  
  
-   Streamübertragungen können die Skalierbarkeit eines Diensts verbessern, indem sie große Speicherpuffer überflüssig machen.Der Einfluss einer Änderung des Übertragungsmodus auf die Skalierbarkeit ist abhängig von der Größe der übertragenen Nachricht.Je größer eine Nachricht ist, desto eher ist eine Streamübertragung zu bevorzugen.  
  
 HTTP, TCP\/IP sowie Named Pipe\-Transporte verwenden gepufferte Übertragungen.In diesem Dokument wird beschrieben, wie Streamingübertragungen anstelle von gepufferten Übertragungen für diese Transporte verwendet werden, und welche Konsequenzen sich daraus ergeben.  
  
## Aktivieren von Streamübertragungen  
 Die Auswahl zwischen der gepufferten Übertragung und der Streamingübertragung erfolgt mithilfe des Transportbindungselements.Das Bindungselement weist eine <xref:System.ServiceModel.TransferMode>\-Eigenschaft auf, die auf `Buffered`, `Streamed`, `StreamedRequest` oder `StreamedResponse` festgelegt werden kann.Wenn Sie den Übertragungsmodus auf `Streamed` festlegen, wird ein Kommunikationsstream in beide Richtungen ermöglicht.Wenn Sie den Übertragungsmodus auf `StreamedRequest` oder `StreamedResponse` festlegen, wird ein Kommunikationsstream nur in der angegebenen Richtung ermöglicht.  
  
 Mit den Bindungen <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding> und <xref:System.ServiceModel.NetNamedPipeBinding> wird die <xref:System.ServiceModel.TransferMode>\-Eigenschaft verfügbar gemacht.Um den Übertragungsmodus für andere Übertragungen festzulegen, müssen Sie eine benutzerdefinierte Bindung erstellen.  
  
 Die Entscheidung über die Verwendung der gepufferten oder der Streamingübertragung wird lokal am Endpunkt getroffen.Bei HTTP\-Übertragungen wird der Übertragungsmodus nicht über Verbindungen oder an Server oder andere Vermittler weitergegeben.Das Festlegen des Übertragungsmodus spiegelt sich nicht in der Beschreibung der Dienstschnittstelle wider.Nachdem Sie eine Clientklasse für einen Dienst erstellt haben, müssen Sie die Konfigurationsdatei für Dienste bearbeiten, die mit Streamingübertragungen verwendet werden sollen, um den Modus festzulegen.Bei TCP und Named Pipe\-Transporten wird der Übertragungsmodus als Richtlinienassertion weitergegeben.  
  
 Codebeispiele finden Sie unter [Vorgehensweise: Aktivieren des Streamingmodus](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## Asynchrones Streaming aktivieren  
 Um asynchrones Streaming zu aktivieren, fügen Sie dem Diensthost das  <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>\-Endpunktverhalten hinzu und legen die Eigenschaft auf `true`<xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> fest.  
  
 Mit dieser WCF\-Version wird die Fähigkeit zum echten asynchronen Streaming auch der Senderseite hinzugefügt.Dies verbessert die Skalierbarkeit des Diensts in Szenarien, in denen Nachrichten an mehrere Clients gestreamt werden, von denen einige eine langsame Lesegeschwindigkeit haben. Dies kann an Netzüberlastung oder daran liegen, dass überhaupt nichts gelesen wird.In diesen Szenarien werden einzelne Threads für den Dienst pro Client nicht blockiert.Dadurch wird sichergestellt, dass der Dienst in der Lage ist, viel mehr Clients zu verarbeiten und somit die Skalierbarkeit des Diensts zu verbessern.  
  
## Einschränkungen für Streamübertragungen  
 Wenn Sie den Streamübertragungsmodus verwenden, werden zusätzliche Einschränkungen von der Laufzeit implementiert.  
  
 Vorgänge, die unter Verwendung einer Streamübertragung ausgeführt werden, können einen Vertrag mit maximal einem Eingabe\- oder Ausgabeparameter aufweisen.Der Parameter entspricht dem gesamten Nachrichtentext, und es muss sich um <xref:System.ServiceModel.Channels.Message>, um einen abgeleiteten Typ von <xref:System.IO.Stream> oder um eine <xref:System.Xml.Serialization.IXmlSerializable>\-Implementierung handeln.Ein Rückgabewert für einen Vorgang entspricht einem Ausgabeparameter.  
  
 Einige Funktionen von [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], darunter zuverlässiges Messaging, Transaktionen und die SOAP\-Nachrichtensicherheit, verwenden gepufferte Nachrichten für Übertragungen.Dadurch können mögliche Leistungsvorteile durch das Streaming reduziert oder zunichte gemacht werden.Mit der Sicherheit auf Transportebene oder mit der Sicherheit auf Transportebene sowie dem Authentifizierungsmodus für die Nachrichtensicherheit können Sie eine Streamübertragung absichern.  
  
 SOAP\-Header werden immer gepuffert, auch wenn eine Streamübertragung verwendet wird.Die Nachrichtenheader dürfen nicht größer sein als das `MaxBufferSize`\-Transportkontingent.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] zu dieser Einstellung finden Sie unter [Transportkontingente](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## Unterschiede zwischen gepufferten und Streamingübertragungen  
 Durch das Ändern des Übertragungsmodus von gepuffert in gestreamt wird auch die systemeigene Kanalform von TCP\- und Named Pipe\-Transporten geändert.Die systemeigene Kanalform für gepufferte Übertragungen ist <xref:System.ServiceModel.Channels.IDuplexSessionChannel>.Die systemeigenen Kanäle für Streamingübertragungen sind <xref:System.ServiceModel.Channels.IRequestChannel> und <xref:System.ServiceModel.Channels.IReplyChannel>.Wenn Sie den Übertragungsmodus in einer bestehenden Anwendung ändern möchten, die diese Transporte unmittelbar \(d. h. nicht über einen Dienstvertrag\) verwendet, müssen Sie die erwartete Kanalform für Kanalfactorys und \-listener ändern.  
  
## Siehe auch  
 [Vorgehensweise: Aktivieren des Streamingmodus](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)