---
title: Beispiel zur schwach typisierten JSON-Serialisierung
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b30e501-4ef5-474d-9fad-a9d559cf9c52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b804064a2b7a7bb0f587ae1dc2014769ca6e058
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2017
---
# <a name="weakly-typed-json-serialization-sample"></a>Beispiel zur schwach typisierten JSON-Serialisierung
Beim Serialisieren eines benutzerdefinierten Typs in ein bestimmtes Übertragungsformat oder beim Deserialisieren eines Übertragungsformats zurück in einen benutzerdefinierten Typ muss der jeweilige benutzerdefinierte Typ für den Dienst und den Client verfügbar sein. Hierzu wird normalerweise das <xref:System.Runtime.Serialization.DataContractAttribute> -Attribut auf diese benutzerdefinierten Typen angewendet, und das <xref:System.Runtime.Serialization.DataMemberAttribute> -Attribut wird auf ihre Member angewendet. Dieser Mechanismus wird auch beim Arbeiten mit JavaScript Object Notation (JSON)-Objekten verwendet, wie im Thema [How to: Serialize and Deserialize JSON Data](../../../../docs/framework/wcf/feature-details/how-to-serialize-and-deserialize-json-data.md)beschrieben.  
  
 In einigen Szenarios muss ein [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] -Dienst oder -Client auf JSON-Objekte zugreifen, die von einem Dienst oder Client außerhalb der Kontrolle des Entwicklers generiert wurden. Da immer mehr Webdienste JSON-APIs öffentlich verfügbar machen, kann es für [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] -Entwickler unpraktisch werden, lokale benutzerdefinierte Typen zu erstellen, in die beliebige JSON-Objekte deserialisiert werden. In diesem Beispiel wird ein Mechanismus bereitgestellt, mit dem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] -Entwickler mit deserialisierten beliebigen JSON-Objekten arbeiten können, ohne benutzerdefinierte Typen zu erstellen. Dies wird als *schwach typisierte Deserialisierung* von JSON-Objekten bezeichnet, da der Typ, in den ein JSON-Objekt deserialisiert wird, zum Zeitpunkt der Kompilierung nicht bekannt ist.  
  
> [!NOTE]
>  Die Setupprozedur und die Buildanweisungen für dieses Beispiel befinden sich am Ende dieses Themas.  
  
 Beispielsweise gibt eine öffentliche Webdienst-API das folgende JSON-Objekt zurück, das Informationen zu einem Benutzer des Diensts enthält.  
  
```json  
{"personal": {"name": "Paul", "age": 23, "height": 1.7, "isSingle": true, "luckyNumbers": [5,17,21]}, "favoriteBands": ["Band ABC", "Band XYZ"]}  
```  
  
 Zum Deserialisieren dieses Objekts muss ein [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] -Client die folgenden benutzerdefinierten Typen implementieren.  
  
```  
[DataContract]  
 public class MemberProfile  
 {  
     [DataMember]  
     public PersonalInfo personal;  
  
     [DataMember]  
     public string[] favoriteBands;  
 }  
  
 [DataContract]  
 public class PersonalInfo  
 {  
     [DataMember]  
     public string name;  
  
     [DataMember]  
     public int age;  
  
     [DataMember]  
     public double height;  
  
     [DataMember]  
     public bool isSingle;  
  
     [DataMember]  
     public int[] luckyNumbers;  
 }  
```  
  
 Dies kann aufwändig sein, insbesondere, wenn der Client mehrere Typen von JSON-Objekten behandeln muss.  
  
 Der in diesem Beispiel bereitgestellte `JsonObject` -Typ führt eine schwach typisierte Darstellung des deserialisierten JSON-Objekts ein. `JsonObject` verwendet die natürliche Zuordnung zwischen JSON-Objekten und [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] -Wörterbüchern und die Zuordnung zwischen JSON-Arrays und [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] -Arrays. Der folgende Code veranschaulicht den `JsonObject` -Typ:  
  
```  
// Instantiation of JsonObject json omitted  
  
string name = json["root"]["personal"]["name"];  
int age = json["root"]["personal"]["age"];  
double height = json["root"]["personal"]["height"];  
bool isSingle = json["root"]["personal"]["isSingle"];  
int[] luckyNumbers = {  
                                     json["root"]["personal"]["luckyNumbers"][0],  
                                     json["root"]["personal"]["luckyNumbers"][1],  
                                     json["root"]["personal"]["luckyNumbers"][2]   
                                 };  
string[] favoriteBands = {  
                                        json["root"]["favoriteBands"][0],  
                                        json["root"]["favoriteBands"][1]  
                                    };  
```  
  
 Sie können JSON-Objekte und -Arrays "durchsuchen", ohne ihren Typ zum Zeitpunkt der Kompilierung deklarieren zu müssen. Eine Erläuterung der Anforderungen für das `["root"]` -Objekt der obersten Ebene finden Sie im Thema [Mapping Between JSON and XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)beschrieben.  
  
> [!NOTE]
>  Die `JsonObject` -Klasse wird nur als Beispiel bereitgestellt. Sie wurde nicht gründlich getestet und sollte nicht in Produktionsumgebungen verwendet werden. Eine offensichtliche Implikation der schwach typisierten JSON-Serialisierung ist der Mangel an Typsicherheit beim Arbeiten mit `JsonObject`.  
  
 Damit der `JsonObject` -Typ verwendet werden kann, muss der Clientvorgangsvertrag <xref:System.ServiceModel.Channels.Message> als Rückgabetyp verwenden.  
  
```  
[ServiceContract]  
    interface IClientSideProfileService  
    {  
        // There is no need to write a DataContract for the complex type returned by the service.  
        // The client will use a JsonObject to browse the JSON in the received message.  
  
        [OperationContract]  
        [WebGet(ResponseFormat = WebMessageFormat.Json)]  
        Message GetMemberProfile();  
    }  
```  
  
 `JsonObject` wird dann instanziiert, wie im folgenden Code dargestellt.  
  
```  
// Code to instantiate IClientSideProfileService channel omitted…  
  
// Make a request to the service and obtain the Json response  
XmlDictionaryReader reader = channel.GetMemberProfile().GetReaderAtBodyContents();  
  
// Go through the Json as though it is a dictionary. There is no need to map it to a .NET CLR type.  
JsonObject json = new JsonObject(reader);  
```  
  
 Der `JsonObject` -Konstruktor nimmt einen <xref:System.Xml.XmlDictionaryReader>an, der durch die <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> -Methode abgerufen wird. Der Reader enthält eine XML-Darstellung der vom Client empfangenen JSON-Nachricht. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] dem Thema [Mapping Between JSON and XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md)beschrieben.  
  
 Das Programm erzeugt die folgende Ausgabe:  
  
```  
Service listening at http://localhost:8000/.  
To view the JSON output from the sample, navigate to http://localhost:8000/GetMemberProfile  
This is Paul's page. I am 23 years old and I am 1.7 meters tall.  
I am single.  
My lucky numbers are 5, 17, and 21.  
My favorite bands are Band ABC and Band XYZ.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>So können Sie das Beispiel einrichten, erstellen und ausführen  
  
1.  Stellen Sie sicher, dass Sie ausgeführt haben die [Setupprozedur für die Windows Communication Foundation-Beispiele zum einmaligen](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Erstellen Sie die Projektmappe "WeaklyTypedJson.sln", wie in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)beschrieben.  
  
3.  Führen Sie die Projektmappe aus.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Ajax\WeaklyTypedJson`  
  
## <a name="see-also"></a>Siehe auch
