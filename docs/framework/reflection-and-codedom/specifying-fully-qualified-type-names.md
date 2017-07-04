---
title: Angeben vollqualifizierter Typnamen | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e1bceed0f95170f9dc11ebc28217b9e8a7dc891c
ms.contentlocale: de-de
ms.lasthandoff: 06/02/2017

---
# <a name="specifying-fully-qualified-type-names"></a>Angeben vollständig gekennzeichneter Typnamen
Sie müssen Typnamen angeben, um eine gültige Eingabe für verschiedene Reflektionsvorgänge zu haben. Ein vollqualifizierter Typname besteht aus der Angabe eines Assemblynamens, eines Namespaces und eines Typnamens. Angaben von Typnamen werden von Methoden wie <xref:System.Type.GetType%2A?displayProperty=fullName>, <xref:System.Reflection.Module.GetType%2A?displayProperty=fullName>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> und <xref:System.Reflection.Assembly.GetType%2A?displayProperty=fullName> verwendet.  
  
## <a name="backus-naur-form-grammar-for-type-names"></a>Backus-Naur-Form-Grammatik für Typnamen  
 Die Backus-Naur-Form (BNF) definiert die Syntax formaler Sprachen. In der folgenden Tabelle werden lexikalische BNF-Regeln aufgelistet, die angeben, wie Sie eine gültige Eingabe erkennen können. Terminale (diejenigen Elemente, die nicht weiter reduziert werden können) werden in Großbuchstaben dargestellt. Nichtterminale (diejenigen Elemente, die noch weiter reduziert werden können) werden in Groß- und Kleinbuchstaben oder durch Zeichenfolgen in einfachen Anführungszeichen dargestellt. Dabei ist das einfache Anführungszeichen (') nicht Teil der Syntax. Das Pipezeichen (&#124;) kennzeichnet Regeln mit Unterregeln.  
  
|BNF-Grammatik für vollqualifizierte Typnamen|  
|-----------------------------------------------|  
|TypeSpec                          :=   ReferenceTypeSpec<br /><br /> &#124;     SimpleTypeSpec|  
|ReferenceTypeSpec            :=   SimpleTypeSpec '&'|  
|SimpleTypeSpec                :=   PointerTypeSpec<br /><br /> &#124;     ArrayTypeSpec<br /><br /> &#124;     TypeName|  
|PointerTypeSpec                :=   SimpleTypeSpec '*'|  
|ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'<br /><br /> &#124;     SimpleTypeSpec '[ReflectionEmitDimension]'|  
|ReflectionDimension           :=   '*'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|ReflectionEmitDimension    :=   '*'<br /><br /> &#124;     Number '..' Anzahl<br /><br /> &#124;     Number '…'<br /><br /> &#124;     ReflectionDimension ',' ReflectionDimension<br /><br /> &#124;     NOTOKEN|  
|Number                            :=   [0-9]+|  
|TypeName                         :=   NamespaceTypeName<br /><br /> &#124;     NamespaceTypeName ',' AssemblyNameSpec|  
|NamespaceTypeName        :=   NestedTypeName<br /><br /> &#124;     NamespaceSpec '.' NestedTypeName|  
|NestedTypeName               :=   IDENTIFIER<br /><br /> &#124;     NestedTypeName '+' IDENTIFIER|  
|NamespaceSpec                 :=   IDENTIFIER<br /><br /> &#124;     NamespaceSpec '.' IDENTIFIER|  
|AssemblyNameSpec           :=   IDENTIFIER<br /><br /> &#124;     IDENTIFIER ',' AssemblyProperties|  
|AssemblyProperties            :=   AssemblyProperty<br /><br /> &#124;     AssemblyProperties ',' AssemblyProperty|  
|AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue|  
  
## <a name="specifying-special-characters"></a>Angeben von Sonderzeichen  
 In einem Typnamen ist IDENTIFIER jeder gültige Name, der durch die Regeln der Sprache vorgegeben wird.  
  
 Verwenden Sie den umgekehrten Schrägstrich (\\) als Escapezeichen, um die folgenden Token abzutrennen, die als Teil von IDENTIFIER verwendet werden.  
  
|Token|Bedeutung|  
|-----------|-------------|  
|\\,|Assemblytrennzeichen|  
|\\+|Trennzeichen für geschachtelte Typen|  
|\\&|Verweistyp|  
|\\*|Zeigertyp|  
|\\[|Arraydimensionstrennzeichen|  
|\\]|Arraydimensionstrennzeichen|  
|\\.|Verwenden Sie den umgekehrten Schrägstrich nur dann vor einem Punkt, wenn der Punkt in einer Arrayspezifikation verwendet wird. Punkte in NamespaceSpec akzeptieren keine umgekehrten Schrägstriche.|  
|\\\|Bei Bedarf kann der umgekehrte Schrägstrich als Zeichenfolgenliteral verwendet werden.|  
  
 Beachten Sie, dass in allen TypeSpec-Komponenten außer AssemblyNameSpec Leerzeichen relevant sind. In AssemblyNameSpec sind Leerzeichen vor dem Trennzeichen „,“ (Komma) relevant, aber dahinter werden sie nicht beachtet.  
  
 Reflektionsklassen, wie z.B <xref:System.Type.FullName%2A?displayProperty=fullName>, geben den beschädigten Namen zurück, damit der zurückgegebene Name in einem Aufruf von <xref:System.Type.GetType%2A> verwendet werden kann, wie in `MyType.GetType(myType.FullName)`.  
  
 Der vollqualifizierte Name eines Typs kann z.B. `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly` sein.  
  
 Wenn der Namespace z.B. `Ozzy.Out+Back` ist, muss vor dem Pluszeichen ein umgekehrter Schrägstrich stehen. Andernfalls interpretiert der Parser dieses als geschachteltes Trennzeichen. Die Reflektion gibt diese Zeichenfolge als `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly` aus.  
  
## <a name="specifying-assembly-names"></a>Angeben von Assemblynamen  
 Eine Assemblynamenspezifikation muss mindestens den wörtlichen Namen (IDENTIFIER) der Assembly enthalten. Auf den IDENTIFIER kann eine durch Kommas getrennte Liste von Eigenschaft/Wert-Paaren folgen, wie in der folgenden Tabelle beschrieben. Das Benennen von IDENTIFIER sollte die Regeln für das Benennen von Dateien einhalten. Beim IDENTIFIER wird Groß- und Kleinschreibung beachtet.  
  
|Name der Eigenschaft|Beschreibung|Zulässige Werte|  
|-------------------|-----------------|----------------------|  
|**Version**|Assemblyversionsnummer|*Major.Minor.Build.Revision*, wobei es sich bei *Major*, *Minor*, *Build* und *Revision* um ganze Zahlen zwischen 0 und einschließlich 65535 handelt|  
|**PublicKey**|Vollständiger öffentlicher Schlüssel|Zeichenfolgenwert des vollständigen öffentlichen Schlüssels im Hexadezimalformat. Geben Sie einen NULL-Verweis an (**Nothing** in Visual Basic), um eine private Assembly explizit zu kennzeichnen.|  
|**PublicKeyToken**|Öffentliches Schlüsseltoken (8-Byte-Hash des vollständigen öffentlichen Schlüssels)|Zeichenfolgenwert des öffentlichen Schlüsseltokens im Hexadezimalformat. Geben Sie einen NULL-Verweis an (**Nothing** in Visual Basic), um eine private Assembly explizit zu kennzeichnen.|  
|**Kultur**|Assemblykultur|Kultur der Assembly im Format RFC-1766 oder auch „neutral“ bei sprachunabhängigen (nicht Satelliten) Assemblys.|  
|**Benutzerdefiniert**|Ein benutzerdefiniertes Binary Large Object (BLOB) Dies wird aktuell nur in Assemblys genutzt, die vom [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) generiert wurden.|Benutzerdefinierte Zeichenfolgen, die vom Native Image Generator-Tool verwendet werden, um den Assemblycache zu informieren, das die Assembly, die gerade installiert wird, ein natives Image ist und deshalb im nativen Imagecache installiert werden muss. Dies wird auch als ZAP-Zeichenfolge bezeichnet.|  
  
 In folgendem Beispiel wird ein **Assemblyname** für eine einfach benannte Assembly mit einer Standardkultur dargestellt.  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 In folgendem Beispiel wird einen vollständig angegebenen Verweis auf eine Assembly mit starkem Namen mit der Kultur „en“ dargestellt.  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 In folgenden Beispielen wird jeweils ein teilweise angegebenen **Assemblyname** dargestellt, der entweder von einer stark oder einfach benannten Assembly erfüllt werden kann.  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 In folgenden Beispielen wird jeweils ein teilweise angegebenen **Assemblyname** dargestellt, der von einer einfach benannten Assembly erfüllt werden muss.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 In folgenden Beispielen wird jeweils ein teilweise angegebenen **Assemblyname** dargestellt, der von einer stark benannten Assembly erfüllt werden muss.  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a>Angeben von Zeigern  
 SimpleTypeSpec* stellt einen nicht verwalteten Zeiger dar. Um z.B. einen Zeiger auf den Typ „MyType“ zu erhalten, verwenden Sie `Type.GetType("MyType*")`. Um einen Zeiger auf den Typ „MyType“ zu erhalten, verwenden Sie `Type.GetType("MyType**")`.  
  
## <a name="specifying-references"></a>Angeben von Verweisen  
 SimpleTypeSpe & stellt einen nicht verwalteten Zeiger oder Verweis dar. Um z.B. einen Verweis auf den Typ „MyType“ zu erhalten, verwenden Sie `Type.GetType("MyType &")`. Beachten Sie, dass Verweise im Gegensatz zu Zeigern auf eine Ebene beschränkt sind.  
  
## <a name="specifying-arrays"></a>Angeben von Arrays  
 In der BNF-Grammatik gilt ReflectionEmitDimension nur für unvollständige Typdefinitionen, die mit <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=fullName> abgerufen wurden. Unvollständige Typdefinitionen sind <xref:System.Reflection.Emit.TypeBuilder>-Objekte, die mit <xref:System.Reflection.Emit?displayProperty=fullName> erstellt wurden, auf denen <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=fullName> jedoch nicht aufgerufen wurde. ReflectionDimension kann verwendet werden, um jede vollständige Typdefinition abzurufen, d.h. jeder geladene Typ.  
  
 Auf Arrays wird in der Reflektion zugegriffen, indem der Rang des Arrays angegeben wird:  
  
-   `Type.GetType("MyArray[]")` ruft ein eindimensionales Array mit der unteren Grenze 0 ab.  
  
-   `Type.GetType("MyArray[*]")` ruft ein eindimensionales Array mit unbekannter unterer Grenze ab.  
  
-   `Type.GetType("MyArray[][]")` ruft das Array eines zweidimensionalen Arrays ab.  
  
-   `Type.GetType("MyArray[*,*]")` und `Type.GetType("MyArray[,]")` rufen ein rechteckiges zweidimensionales Array mit unbekannter unterer Grenze ab.  
  
 Beachten Sie `MyArray[] != MyArray[*]`, aus Perspektive der Runtime, aber für mehrdimensionale Arrays sind die beiden Notationen gleich. D.h., `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` ergibt **TRUE**.  
  
 `MyArray[0..5]` gibt für **ModuleBuilder.GetType** ein eindimensionales Array mit der Größe 6 und einer unteren Grenze von 0 an. `MyArray[4…]` gibt ein eindimensionales Array mit unbekannter Größe und einer unteren Grenze von 4 an.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Reflection.AssemblyName>   
 <xref:System.Reflection.Emit.ModuleBuilder>   
 <xref:System.Reflection.Emit.TypeBuilder>   
 <xref:System.Type.FullName%2A?displayProperty=fullName>   
 <xref:System.Type.GetType%2A?displayProperty=fullName>   
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=fullName>   
 [Anzeigen von Typinformationen](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)