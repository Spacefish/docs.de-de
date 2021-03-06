---
title: "Veröffentlichen und Abrufen von Metadaten über eine benutzerdefinierte Bindung"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f66821f38e8915ee93cf5b1b77dd75e32662121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Veröffentlichen und Abrufen von Metadaten über eine benutzerdefinierte Bindung
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> bietet Support für das Hinzufügen von Metadatenendpunkten zu einem Dienst. Diese Metadatenendpunkte können reagieren auf HTTP GET-Anforderungen an eine URL, die verfügt über eine `?wsdl` Querystring und WS-Transfer GET-Anforderungen, wie in der WS-MetadataExchange (MEX)-Spezifikation definiert. MEX-Endpunkte implementieren den <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType>-Vertrag.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Veröffentlichen von Metadaten über eine benutzerdefinierte Bindung  
 Die HTTP GET-Metadatenendpunkte und HTTPS GET-Metadatenendpunkte werden durch Festlegen der <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType>-Eigenschaften oder <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType>-Eigenschaften auf `true` aktiviert. Die Bindungen für diese Endpunkte können nicht konfiguriert werden.  
  
 Der <xref:System.ServiceModel.Description.IMetadataExchange>-Vertrag kann jedoch mit anderen Endpunkten, auch Endpunkten, die benutzerdefinierte Bindungen verwenden, verwendet werden, da <xref:System.ServiceModel.Description.IMetadataExchange>-Endpunkte sich nicht von anderen [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]-Dienstendpunkten unterscheiden. Wenn Sie wissen, wie Sie die Konfiguration einer vom System bereitgestellten Bindung ändern können oder wie Sie eine <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> konfigurieren können, dann können Sie eine Bindung so konfigurieren, dass sie mit einem <xref:System.ServiceModel.Description.IMetadataExchange>-Endpunkt verwendet werden kann.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Abrufen von Metadaten über eine benutzerdefinierte Bindung  
 Metadaten können von HTTP Get-Metadatenendpunkten und HTTPS Get-Metadatenendpunkten mit Standard-HTTP-Anforderungen bzw. HTTPS-GET-Anforderungen abgerufen werden.  
  
 Um Metadaten von einem MEX-Metadatenendpunkt abzurufen, können Sie im Allgemeinen eine der Standard-MEX-Bindungen, die von [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] unterstützt werden, verwenden. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. Der <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType>-Typ und das Tool "Svcutil.exe" wählen automatisch eine dieser Standard-MEX-Bindungen basierend auf der Adresse des angegebenen Metadatenendpunkts aus.  
  
 Wenn ein MEX-Metadatenendpunkt eine andere Bindung als eine der Standard-MEX-Bindungen verwendet, können Sie die vom <xref:System.ServiceModel.Description.MetadataExchangeClient> verwendete Bindung mit Code oder über die Angabe einer <xref:System.ServiceModel.Description.IMetadataExchange>-Clientendpunktkonfiguration konfigurieren. Das Tool Svcutil.exe lädt automatisch aus der Konfigurationsdatei eine <xref:System.ServiceModel.Description.IMetadataExchange>-Clientendpunktkonfiguration, die den gleichen Namen hat wie das URI-Schema für die Metadatenendpunktadresse.  
  
## <a name="security"></a>Sicherheit  
 Stellen Sie beim Veröffentlichen von Metadaten über eine benutzerdefinierte Bindung sicher, dass die Bindung den Sicherheitssupport bietet, der für die Metadaten erforderlich ist. Um beispielsweise die Offenlegung von Informationen zu verhindern und sicherzustellen, dass der Client die Berechtigung hat, die Metadaten abzurufen, können Sie die Metadaten und die Anwendung weiter sichern, indem Sie den <xref:System.ServiceModel.Description.IMetadataExchange>-Endpunkt so konfigurieren, dass eine Authentifizierung und Verschlüsselung notwendig sind. Im Beispiel [benutzerdefinierter sicherer Metadatenendpunkt](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) wird dieses Szenario veranschaulicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von Diensten](../../../../docs/framework/wcf/securing-services.md)  
 [WS-MetadataExchange-Bindungen](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [Vorgehensweise: Konfigurieren einer benutzerdefinierten WS-Metadata Exchange-Bindung](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [Vorgehensweise: Abrufen von Metadaten über eine nicht - MEX-Bindung](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
