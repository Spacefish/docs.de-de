---
title: "&lt;Hinzufügen&gt; -Element für SchemeSettings (Uri-Einstellungen)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 8ce4cc33d054e74fc9868a16764e744daf260c10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a>&lt;Hinzufügen&gt; -Element für SchemeSettings (Uri-Einstellungen)
Fügt eine Schema-Einstellung für den Schemanamen eines.  
  
 \<configuration>  
\<URI >  
\<SchemeSettings >  
\<add>  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente sowie übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Name|Der Schemaname für die diese Einstellung gilt. Der nur die unterstützten Werte sind Name = "http" und Name = "Https".|  
  
## <a name="attribute-name-attribute"></a>{Attributnamen} Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|genericUriParserOptions|Die Parseroptionen für dieses Schema. Der nur unterstützte Wert GenericUriParserOptions ist = "DontUnescapePathDotsAndSlashes".|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<schemeSettings>-Element (URI-Einstellungen)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Gibt an, ob <xref:System.Uri> auf bestimmte Schemen analysiert wird.|  
  
## <a name="remarks"></a>Hinweise  
 Wird standardmäßig die <xref:System.Uri?displayProperty=nameWithType> Klasse un-Escapezeichen Prozent codiert Pfadtrennzeichen vor dem Pfad Komprimierung ausführen. Dies wurde als Sicherheitsmechanismus vor Angriffen wie folgt implementiert:  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Wenn dieser URI übergeben wird auf Module nicht behandeln Prozent codierten Zeichen richtig, kann dies dazu führen den folgenden Befehl, der vom Server ausgeführt wird:  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 Aus diesem Grund <xref:System.Uri?displayProperty=nameWithType> -Klasse erste un-Escapezeichen Pfadtrennzeichen und wendet dann Pfad Komprimierung. Das Ergebnis der Übergabe der böswilligen URL oben auf <xref:System.Uri?displayProperty=nameWithType> Klassenkonstruktor führt der folgende URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 Dieses Standardverhalten kann auf keine Escapezeichen Prozentzeichen codierten Pfadtrennzeichen mithilfe der Konfigurationsoption SchemeSettings für ein bestimmtes Schema geändert werden.  
  
## <a name="configuration-files"></a>Konfigurationsdateien  
 Dieses Element kann in der Anwendungskonfigurationsdatei oder in der Computerkonfigurationsdatei ("Machine.config") verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Konfiguration von verwendet die <xref:System.Uri> Klasse keine Escapezeichen Prozentzeichen codiert Pfadtrennzeichen für die http-Protokollschema unterstützt.  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [Network Settings Schema (Schema für Netzwerkeinstellungen)](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
