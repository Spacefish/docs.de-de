---
title: '&lt;"Provideroption"&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: "22"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 3a01a64ab8828104e8404f7d4efdd7b37eea373e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="ltprovideroptiongt-element"></a>&lt;"Provideroption"&gt; Element
Gibt die Version Compilerattribute für einen Sprachanbieter an.  
  
 \<Konfiguration-Element >  
\<System.CodeDom-Element >  
\<Compilers-Element >  
\<Compilerfehler >-Element  
\<"Provideroption" >-Element  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderliches Attribut.<br /><br /> Gibt den Namen der Option. Beispiel: "CompilerVersion".|  
|`value`|Erforderliches Attribut.<br /><br /> Gibt den Wert für die Option an. z. B. "v3. 5".|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[\<configuration>-Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Das Stammelement in jeder Konfigurationsdatei, die von der Common Language Runtime und den .NET Framework-Anwendungen verwendet wird.|  
|[\<System.CodeDom > Element](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Gibt die Compilerkonfigurationseinstellungen für verfügbare Sprachanbieter an.|  
|[\<Compiler >-Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Container für compilerkonfigurationselemente; enthält 0 (null) oder mehrere `<compiler>` Elemente.|  
|[\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Gibt die Compilerkonfigurationsattribute für einen Sprachanbieter an.|  
  
## <a name="remarks"></a>Hinweise  
 In .NET Framework, Version 3.5, Codeanbieter Code Document Object Model (CodeDOM) anbieterspezifischen Optionen mit Unterstützung der `<providerOption>` Element.  
  
 .NET Framework 3.5 enthält aktualisierte .NET Framework 2.0-Assemblys sowie neue Version 3.5-Assemblys, die neue Typen enthalten. Microsoft c# und Visual Basic-Codeanbieter in .NET Framework 2.0-Assemblys enthalten sind, jedoch wurden aktualisiert, um Version 3.5-Compiler unterstützen. Standardmäßig generiert die aktualisierten Codeanbieter Code für Compiler der Version 2.0. Sie können die `<providerOption>` Element so ändern Sie die Zielversion der Compiler auf 3.5. Zu diesem Zweck geben Sie "CompilerVersion" für die `name` Attribut und "v3. 5" für die `value` Attribut. Sie müssen die Versionsnummer mit einem Kleinbuchstaben "V" voranstellen.  
  
 Sie können die Spezifikation der Version globale vornehmen, durch Hinzufügen der `<providerOption>` Elements, das das .NET Framework 2.0 "Machine.config" oder der Stammdatei "Web.config". Wenn Sie die Standardversion der Compiler auf 3.5 in der Datei "Machine.config" zu aktualisieren, können Sie es wieder zu 2.0 für eine einzelne Anwendung ändern, mit der `<providerOption>` Element in der Anwendungskonfigurationsdatei.  
  
 CodeDOM Code Anbieterimplementierer verarbeiten benutzerdefinierte Optionen, wenn einen Konstruktor bereitstellen, akzeptiert eine `providerOptions` Parameter vom Typ <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht das angeben, Version 3.5 von C#-Code-Anbieters verwendet werden soll.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Konfigurationsdateischema](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<Compiler >-Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Specifying Fully Qualified Type Names (Angeben vollqualifizierter Typnamen)](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [Compiler-Element für Compiler für Kompilierung ((ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
