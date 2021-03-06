---
title: '&lt;SupportedRuntime&gt; Element'
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5c38dc87d6015f0c814ea319c9353ea757478b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="ltsupportedruntimegt-element"></a>&lt;SupportedRuntime&gt; Element
Gibt an, welche Versionen der Common Language Runtime von der Anwendung unterstützt werden. Dieses Element sollte von allen Anwendungen verwendet werden, die mit Version 1.1 oder höher von .NET Framework erstellt wurden.  
  
[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  

[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
  
**\<supportedRuntime>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**version**|Optionales Attribut.<br /><br /> Ein Zeichenfolgenwert, der die Version der Common Language Runtime (CLR) angibt, die diese Anwendung unterstützt. Gültige Werte von der `version` -Attribut angegeben wird, finden Sie unter der ["Runtime Version"-Werte](#version) Abschnitt. **Hinweis:** über .NET Framework 3.5, die "*Laufzeitversion*" Wert hat das Format *wichtigen*. *kleinere*. *Erstellen Sie*. Beginnend mit [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] sind nur die Haupt- und Nebenversionsnummern erforderlich (d. h. "v4.0"anstelle von "v4.0.30319"). Die kürzere Zeichenfolge wird empfohlen.|  
|**SKU**|Optionales Attribut.<br /><br /> Ein Zeichenfolgenwert, der die SKU (Stock Keeping Unit) angibt, die wiederum angibt, welche .NET Framework-Version von dieser Anwendung unterstützt wird.<br /><br /> Beginnend mit .NET Framework 4.0, die Verwendung der `sku` -Attributs empfohlen.  Wenn vorhanden, gibt es die Version des .NET Frameworks an, auf die die App aufgerichtet ist.<br /><br /> Gültige Werte des Sku-Attributs finden Sie unter der ["Sku Id"-Werte](#sku) Abschnitt.|  
  
## <a name="remarks"></a>Hinweise  
Wenn die  **\<SupportedRuntime >** -Element nicht in der Anwendungskonfigurationsdatei vorhanden ist, die Version der Laufzeit verwendet, die zum Erstellen der Anwendung verwendet wird.  

Die  **\<SupportedRuntime >** -Element sollte von allen Anwendungen, die mit Version 1.1 oder höher der Runtime erstellt verwendet werden. Anwendungen, die nur Version 1.0 der Laufzeit unterstützen müssen verwenden die [ \<RequiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) Element.  
  
> [!NOTE]
>  Bei Verwendung der [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) Funktion, um die Konfigurationsdatei angeben, müssen Sie die `<requiredRuntime>` -Element für alle Versionen der Laufzeit. Die `<supportedRuntime>` Element wird ignoriert, wenn Sie [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).  
  
Bei Apps, die Versionen der Laufzeit aus .NET Framework 1.1 bis 3.5 unterstützen, sollte, wenn mehrere Versionen der Laufzeit unterstützt werden, das erste Element die bevorzugte Version der Laufzeit angeben, und das letzte die am wenigsten bevorzugte Version. Für apps, die .NET Framework 4.0 oder höhere Versionen unterstützen, die `version` Attribut gibt an, die CLR-Version, die für die .NET Framework 4 und höheren Versionen ist, und die `sku` Attribut gibt die einzelnen .NET Framework-Version an, die die app Ziele.  
  
> [!NOTE]
>  Wenn Ihre Anwendung legacy-Aktivierungspfade, z. B. verwendet die [CorBindToRuntimeEx-Funktion](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), und Sie möchten diese Pfade Version 4 der CLR anstelle von einer früheren Version aktivieren, oder wenn Ihre Anwendung mit der erstelltwird[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]aber eine Abhängigkeit auf eine Assembly im gemischten Modus mit einer früheren Version von .NET Framework erstellt es reicht nicht aus, geben Sie die [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] in der Liste der unterstützten Laufzeiten. Darüber hinaus werden in der [ \<Startup > Element](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in der Konfigurationsdatei müssen Sie festlegen der `useLegacyV2RuntimeActivationPolicy` -Attribut auf `true`. Wenn jedoch dieses Attribut auf `true` festgelegt ist, werden alle Komponenten, die mit früheren Versionen von .NET Framework erstellt wurden, mit [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ausgeführt statt den Laufzeiten, mit denen sie erstellt wurden.  
  
Es wird empfohlen, dass Sie die Anwendungen mit allen .NET Framework-Versionen testen, in denen sie ausgeführt werden können.  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a>„runtime version“-Werte  
Die `runtime` Attribut gibt an, die Common Language Runtime (CLR)-Version, die für eine bestimmte Anwendung erforderlich ist. Beachten Sie, die allen Versionen von .NET Framework 4.x angeben der `v4.0` CLR. Die folgende Tabelle enthält die gültigen Werte für die *Laufzeitversion* Wert, der die `version` Attribut.  

|.NET Framework-Version|`version`-Attribut|  
|----------------------------|-------------------------|  
|1,0|"v1.0.3705"|  
|1,1|"v1.1.4322"|  
|2,0|"v2.0.50727"|  
|3,0|"v2.0.50727"|  
|3,5|"v2.0.50727"|  
|4.0-4.7.1|"v4.0"|  

  
<a name="sku"></a>   
## <a name="sku-id-values"></a>"sku id"-Werte  
Die `sku` Attribut verwendet eine Zielframeworkmoniker (TFM), um die Version von .NET Framework anzugeben, die die app als Ziel verwendet und erfordert zum Ausführen. Die folgende Tabelle enthält die gültigen Werte sind die unterstützten durch die `sku` -Attribut, beginnend mit .NET Framework 4.
  
|.NET Framework-Version|`sku`-Attribut|  
|----------------------------|---------------------|  
|4.0|".NETFramework,Version=v4.0"|  
|4.0, Clientprofil|".NETFramework,Version=v4.0,Profile=Client"|  
|4.0, Plattformupdate 1|.NETFramework, Version=v4.0.1|  
|4.0, Clientprofil, Update 1|.NETFramework, Version=v4.0.1, Profile=Client|  
|4.0, Plattformupdate 2|.NETFramework, Version=v4.0.2|  
|4.0, Clientprofil, Update 2|.NETFramework, Version=v4.0.2, Profile=Client|  
|4.0, Plattformupdate 3|.NETFramework, Version=v4.0.3|  
|4.0, Clientprofil, Update 3|.NETFramework, Version=v4.0.3, Profile=Client|  
|4.5|".NETFramework,Version=v4.5"|  
|4.5.1|".NETFramework,Version=v4.5.1"|  
|4.5.2|".NETFramework,Version=v4.5.2"|  
|4.6|".NETFramework,Version=v4.6"|  
|4.6.1|".NETFramework,Version=v4.6.1"|  
|4.6.2|". NETFramework, Version = V4.6.2 "|  
|4.7|". NETFramework, Version = 4.7 "|
|4.7.1|". NETFramework, Version = 4.7.1"|

## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht, wie Sie die unterstützte Laufzeitversion in einer Konfigurationsdatei angeben. Die Konfigurationsdatei gibt an, dass die app auf die .NET Framework-4.7 abzielt.  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />  
   </startup>  
</configuration>  
```  
  
## <a name="configuration-file"></a>Konfigurationsdatei  
 Dieses Element kann in der Anwendungskonfigurationsdatei verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Startup Settings Schema (Schema für Starteinstellungen)](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [Konfigurationsdateischema](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Prozessinterne parallele Ausführung](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
