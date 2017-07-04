---
title: "&lt;transport&gt; von &lt;netHttpBinding&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;transport&gt; von &lt;netHttpBinding&gt;
Definiert Eigenschaften, die Authentifizierungsparameter für den HTTP\-Transport steuern.  
  
## Syntax  
  
```  
<netHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</basicHttpBinding>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|clientCredentialType|-   Gibt den Typ der Anmeldeinformationen an, die beim Durchführen der Clientauthentifizierung mit HTTP\-Authentifizierung verwendet werden.  Die Standardeinstellung ist `None`.  Dieses Attribut ist vom Typ <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-   Gibt den Anmeldeinformationstyp an, der bei der Clientauthentifizierung mit einem Proxy über HTTP innerhalb einer Domäne verwendet werden soll.  Dies Attribut trifft nur zu, wenn das `mode`\-Attribut dieses übergeordneten `security`\-Elements `Transport` oder `TransportCredentialsOnly` lautet.  Dieses Attribut ist vom Typ <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|realm|Eine Zeichenfolge, die den vom HTTP\-Authentifizierungsschema verwendeten Bereich für die Digest\- oder Standardauthentifizierung angibt.  Der Standardwert ist eine leere Zeichenfolge.|  
|policyEnforcement|Diese Enumeration gibt an, wann die <xref:System.Security.Authentication.ExtendedProtectionPolicy> erzwungen werden soll.<br /><br /> 1.  Never – die Richtlinie wird nie erzwungen \(erweiterter Schutz ist deaktiviert\).<br />2.  WhenSupported – die Richtlinie wird nur erzwungen, wenn der Client erweiterten Schutz unterstützt.<br />3.  Always – die Richtlinie wird immer erzwungen.  Clients, die erweiterten Schutz nicht unterstützen, werden nicht authentifiziert.|  
|protectionScenario|Diese Enumeration gibt das von der Richtlinie erzwungene Schutzszenario an.|  
  
## clientCredentialType\-Attribut  
  
|Wert|Beschreibung|  
|----------|------------------|  
|Keine|Nachrichten werden nicht während der Übertragung gesichert.|  
|Standard|Gibt die Standardauthentifizierung an.|  
|Digest|Gibt die Digestauthentifizierung an.|  
|Ntlm|Gibt die NTLM\-Authentifizierung an, wenn möglich, und ob die Windows\-Authentifizierung fehlschlägt.|  
|Windows|Gibt die integrierte Windows\-Authentifizierung an.|  
  
## proxyCredentialType\-Attribut  
  
|Wert|Beschreibung|  
|----------|------------------|  
|Keine|-   Nachrichten werden nicht während der Übertragung gesichert.|  
|Standard|Gibt die Standardauthentifizierung an, wie definiert in RFC 2617 – HTTP Authentication: Basic and Digest Authentication.|  
|Digest|Gibt die Digestauthentifizierung an, wie definiert in RFC 2617 – HTTP Authentication: Basic and Digest Authentication.|  
|Ntlm|Gibt die NTLM\-Authentifizierung an, wenn möglich, und ob die Windows\-Authentifizierung fehlschlägt.|  
|Windows|Gibt die integrierte Windows\-Authentifizierung an.|  
|Zertifikat|Führt die Clientauthentifizierung mit einem Zertifikat aus.  Diese Option funktioniert nur, wenn das `Mode`\-Attribut des übergeordneten `security`\-Elements auf Transport gesetzt ist. Sie funktioniert nicht, wenn es auf TransportCredentialOnly gesetzt ist.|  
  
### Untergeordnete Elemente  
 Keine  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[\<Sicherheit\>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|Definiert die Sicherheitsfunktionen für [\<netHttpBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).|  
  
## Beispiel  
 Im folgenden Beispiel wird die Verwendung der SSL\-Transportsicherheit mit der Standardbindung veranschaulicht.  Standardmäßig unterstützt die Standardbindung die HTTP\-Kommunikation.  
  
```  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint address=""  
               binding="netHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
   </services>  
    <bindings>  
        <netHttpBinding>  
        <!-- Configure basicHttpBinding with Transport security -- >  
        <!-- mode and clientCredentialType set to None.-->  
           <binding name="Binding1">  
               <security mode="Transport">  
                   <transport clientCredentialType="None"  
                              proxyCredentialType="None">  
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </netHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## Siehe auch  
 <xref:System.ServiceModel.Configuration.NetHttpSecurityElement.Transport%2A>   
 <xref:System.ServiceModel.NetHttpSecurity.Transport%2A>   
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>   
 <xref:System.ServiceModel.HttpTransportSecurity>   
 [Sichern von Diensten und Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)   
 [Bindungen](../../../../../docs/framework/wcf/bindings.md)   
 [Konfigurieren der vom System bereitgestellten Bindungen](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)   
 [Using Bindings to Configure Windows Communication Foundation Services and Clients](http://msdn.microsoft.com/de-de/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<Bindung\>](../../../../../docs/framework/misc/binding.md)