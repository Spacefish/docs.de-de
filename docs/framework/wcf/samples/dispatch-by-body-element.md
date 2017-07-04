---
title: "Verteilen nach Textelement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Verteilen nach Textelement
Dieses Beispiel veranschaulicht, wie ein alternativer Algorithmus zum Zuweisen eingehender Nachrichten zu Vorgängen implementiert wird.  
  
 Standardmäßig wählt der Dienstmodellverteiler die passende Verarbeitungsmethode für eine eingehende Nachricht auf der Grundlage des WS\-Adressierungsaktionsheaders der Nachricht aus bzw. auf der Grundlage der entsprechenden Informationen in der HTTP SOAP\-Anforderung.  
  
 Einige SOAP 1.1\-Webdienststapel, die nicht den WS\-I Basic Profile 1.1\-Richtlinien folgen, verteilen Nachrichten nicht auf der Grundlage des Aktions\-URIs, sondern auf der Grundlage des qualifizierten XML\-Namens des ersten Elements innerhalb des SOAP\-Nachrichtentexts.  Gleichzeitig kann die Clientseite dieser Stapel Nachrichten mit einem leeren oder beliebigen HTTP SoapAction\-Header senden, da dies mit den SOAP 1.1\-Spezifikationen zulässig ist.  
  
 Um das Verfahren zu ändern, mit dem Nachrichten an Methoden verteilt werden, implementiert das Beispiel die <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>\-Erweiterbarkeitsschnittstelle auf dem `DispatchByBodyElementOperationSelector`.  Diese Klasse wählt Operationen auf der Grundlage des ersten Elements des Nachrichtentexts aus.  
  
 Der Konstruktor erwartet ein mit Paaren von `XmlQualifiedName` und Zeichenketten gefülltes Wörterbuch, dabei geben die qualifizierten Namen den Namen des ersten untergeordneten Elements des SOAP\-Nachrichtentexts an, und die Zeichenketten geben den entsprechenden Vorgangsnamen an.  Der `defaultOperationName` ist der Name des Vorgangs, der alle Nachrichten empfängt, die nicht mit diesem Wörterbuch abgeglichen werden können.  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>\-Implementierungen sind sehr einfach zu erstellen, da die Schnittstelle nur eine Methode besitzt: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.  Die Aufgabe dieser Methode ist, eingehende Nachrichten zu überprüfen und eine Zeichenkette zurückzugeben, die dem Namen einer Methode auf dem Dienstvertrag für den aktuellen Endpunkt entspricht.  
  
 In diesem Beispiel ruft die Vorgangsauswahl mithilfe von <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> einen <xref:System.Xml.XmlDictionaryReader> für den Text der eingehenden Nachricht ab.  Diese Methode setzt den Leser bereits auf das erste untergeordnete Element des Nachrichtentexts, sodass es ausreicht, den aktuellen Namen des Elements und den Namespace\-URI abzurufen und diese zu einem `XmlQualifiedName` zu kombinieren, der dann für die Suche nach dem entsprechenden Vorgang aus dem Wörterbuch der Vorgangsauswahl verwendet wird.  
  
```  
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 Wenn mit <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> oder einer der anderen Methoden, die Zugriff auf den Nachrichtentext haben, auf den Nachrichtentext zugegriffen wird, wird die Nachricht als "gelesen" markiert, was bedeutet, dass die Nachricht für weitere Verarbeitung nicht mehr zur Verfügung steht.  Daher erstellt die Vorgangsauswahl mithilfe der im folgenden Code dargestellten Methode eine Kopie der eingehenden Nachricht.  Da die Position des Lesers während der Überprüfung nicht geändert wurde, kann auf diesen durch die neu erstellte Nachricht verwiesen werden, in die auch die Nachrichteneigenschaften und die Nachrichtenheader kopiert werden, sodass eine exakte Kopie der ursprünglichen Nachricht entsteht.  
  
```  
  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
  
```  
  
## Hinzufügen einer Vorgangsauswahl zu einem Dienst  
 Dienstverteilungs\-Vorgangsauswahlen sind Erweiterungen für den [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]\-Verteiler.  Für die Auswahl von Methoden auf dem Rückrufkanal von Duplexverträgen stehen auch Clientvorgangsauswahlen zur Verfügung, die ähnlich funktionieren wie die hier erläuterten Verteilungsvorgangsauswahlen, die jedoch nicht explizit in diesem Beispiel behandelt werden.  
  
 Wie die meisten Dienstmodellerweiterungen werden auch Verteilungsvorgangsauwahlen dem Verteiler mithilfe von Verhaltensweisen hinzugefügt.  Ein *Verhalten* ist ein Konfigurationsobjekt, das der Verteilungslaufzeit \(oder der Clientlaufzeit\) eine oder mehrere Erweiterungen hinzufügt oder die Einstellungen auf andere Weise ändert.  
  
 Da Vorgangsauswahlen Vertragsbereiche besitzen, ist das entsprechende Verhalten, das hier implementiert wird, <xref:System.ServiceModel.Description.IContractBehavior>.  Da die Schnittstelle auf einer von <xref:System.Attribute> abgeleiteten Klasse implementiert wird, wie im folgenden Code dargestellt, kann das Verhalten deklarativ zu jedem Dienstvertrag hinzugefügt werden.  Immer wenn ein <xref:System.ServiceModel.ServiceHost> geöffnet und die Verteilungslaufzeit erstellt wird, werden alle Verhalten, die als Attribute auf Verträgen, Vorgängen und Dienstimplementierungen oder als Element in der Dienstkonfiguration gefunden werden, automatisch hinzugefügt und der Reihe nach auf Erweiterungen oder Änderungen der Standardkonfiguration abgefragt.  
  
 Der Kürze wegen zeigt der folgende Codeauszug nur die Implementierung der Methode <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, die die Konfigurationsänderung für den Verteiler in diesem Beispiel bewirkt.  Die anderen Methoden werden nicht dargestellt, da sie zum Aufrufer zurückkehren, ohne eine Aufgabe auszuführen.  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 Zuerst richtet die <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>\-Implementierung das Suchwörterbuch für die Vorgangsauswahl ein, indem die <xref:System.ServiceModel.Description.OperationDescription>\-Elemente in der <xref:System.ServiceModel.Description.ContractDescription> der Dienstendpunkte durchlaufen werden.  Anschließend wird jede Vorgangsauswahl auf das Vorhandensein des `DispatchBodyElementAttribute`\-Verhaltens untersucht, einer Implementierung von<xref:System.ServiceModel.Description.IOperationBehavior>, das ebenfalls im Beispiel definiert ist.  Diese Klasse ist zwar ebenfalls ein Verhalten, sie ist jedoch passiv und bewirkt keine aktiven Konfigurationsänderungen an der Verteilungslaufzeit.  All ihre Methoden kehren zum Aufrufer zurück, ohne eine Aktion auszuführen.  Das Vorgangsverhalten ist nur vorhanden, damit die für den neuen Verteilungsmechanismus erforderlichen Metadaten – d. h. der qualifizierte Name des Textelements, bei dessen Auftreten ein Vorgang ausgewählt wird – den entsprechenden Vorgängen zugeordnet werden können.  
  
 Wenn ein solches Verhalten gefunden wird, werden dem Wörterbuch ein aus dem qualifizierten XML\-Namen gebildetes Wertepaar \(`QName`\-Eigenschaft\) und der Vorgangsname \(`Name`\-Eigenschaft\) hinzugefügt.  
  
 Nachdem das Wörterbuch gefüllt wurde, wird eine neue `DispatchByBodyElementOperationSelector` mit diesen Informationen erstellt und als Vorgangsauswahl der Verteilungslaufzeit festgelegt:  
  
```  
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## Implementieren des Diensts  
 Das in diesem Beispiel implementierte Verhalten wirkt sich unmittelbar darauf aus, wie übermittelte Nachrichten interpretiert und verteilt werden. Dies ist eine Funktion des Dienstvertrags.  Daher sollte das Verhalten auf Dienstvertragsebene in jeder Dienstimplementierung deklariert werden, die das Verhalten verwendet.  
  
 Der Beispielprojektdienst wendet das `DispatchByBodyElementBehaviorAttribute`\-Vertragsverhalten auf den `IDispatchedByBody`\-Dienstvertrag an und bezeichnet jede der beiden Vorgänge `OperationForBodyA()` und `OperationForBodyB()` mit einem `DispatchBodyElementAttribute`\-Vorgangsverhalten.  Wenn ein Diensthost für einen Dienst, der diesen Vertrag implementiert, geöffnet wird, werden diese Metadaten von dem Verteilungsersteller wie zuvor erläutert ausgewählt.  
  
 Da die Vorgangsauswahl die Verteilung nur auf der Grundlage des Nachrichtentexts ausführt und die "Aktion" ignoriert, muss der Laufzeit mitgeteilt werden, nicht die Aktionsheader in den zurückgegebenen Antworten zu überprüfen. Weisen Sie dazu der `ReplyAction`\-Eigenschaft von <xref:System.ServiceModel.OperationContractAttribute> den Platzhalter "\*" zu.  Außerdem muss ein Standardvorgang vorhanden sein, dessen Aktionseigenschaft auf den Platzhalter "\*" festgelegt ist.  Der Standardvorgang empfängt alle Nachrichten, die nicht verteilt werden können und kein `DispatchBodyElementAttribute` besitzen:  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 Die Beispieldienstimplementierung ist einfach.  Jede Methode schließt die empfangene Nachricht in eine Antwortnachricht ein und sendet sie zurück an den Client.  
  
## Erstellen und Ausführen des Beispiels  
 Wenn Sie das Beispiel ausführen, wird der Textinhalt der Vorgangsantworten im Clientkonsolenfenster angezeigt, ähnlich der folgenden \(formatierten\) Ausgabe.  
  
 Der Client sendet drei Nachrichten an den Dienst, dessen Textinhaltselemente entsprechend mit `bodyA`, `bodyB` und `bodyX` benannt werden.  Wie aus der vorstehenden Beschreibung und dem dargestellten Dienstvertrag hervorgeht, wird die eingehende Nachricht mit dem `bodyA`\-Element an die `OperationForBodyA()`\-Methode weitergeleitet.  Da kein explizites Verteilungsziel für die Nachricht mit dem Textelement `bodyX` vorhanden ist, wird die Nachricht an den `DefaultOperation()` weitergeleitet.  Jeder der Dienstvorgänge schließt den empfangenen Nachrichtentext in ein Element ein, das spezifisch für die Methode ist, und sendet ihn zurück. Dies dient dazu, dass sich Eingangs\- und Ausgangsnachricht in diesem Beispiel eindeutig entsprechen.  
  
```  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
  
```  
  
#### So können Sie das Beispiel einrichten, erstellen und ausführen  
  
1.  Stellen Sie sicher, dass Sie die [Einmaliges Setupverfahren für Windows Communication Foundation\-Beispiele](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) ausgeführt haben.  
  
2.  Befolgen Sie die Anweisungen unter [Erstellen der Windows Communication Foundation\-Beispiele](../../../../docs/framework/wcf/samples/building-the-samples.md), um die Projektmappe zu erstellen.  
  
3.  Um das Beispiel in einer Konfiguration mit einem Computer oder computerübergreifend auszuführen, befolgen Sie die Anweisungen unter [Durchführen der Windows Communication Foundation\-Beispiele](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert.  Suchen Sie nach dem folgenden Verzeichnis \(Standardverzeichnis\), bevor Sie fortfahren.  
>   
>  `<Installationslaufwerk>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation \(WCF\) and Windows Workflow Foundation \(WF\) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]\- und [!INCLUDE[wf1](../../../../includes/wf1-md.md)]\-Beispiele herunterzuladen.  Dieses Beispiel befindet sich im folgenden Verzeichnis.  
>   
>  `<Installationslaufwerk>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## Siehe auch