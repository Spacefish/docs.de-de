---
title: "&lt;Deaktivieren Sie&gt; -Element für &lt;\"configSections\"&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 70fc73c9e97274ac1165950038ee509fa8f2f9c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="52120-102">\<Deaktivieren Sie >-Element für \<ConfigSections ></span><span class="sxs-lookup"><span data-stu-id="52120-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="52120-103">Löscht alle zuvor definierten Abschnitte und Abschnittsgruppen.</span><span class="sxs-lookup"><span data-stu-id="52120-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="52120-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="52120-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="52120-105">&nbsp;&nbsp;[**\<ConfigSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="52120-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="52120-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Deaktivieren Sie >**</span><span class="sxs-lookup"><span data-stu-id="52120-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="52120-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="52120-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="52120-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="52120-108">Attribute</span></span>

|           | <span data-ttu-id="52120-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="52120-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="52120-110">**name**</span><span class="sxs-lookup"><span data-stu-id="52120-110">**name**</span></span>  | <span data-ttu-id="52120-111">Erforderliches Attribut.</span><span class="sxs-lookup"><span data-stu-id="52120-111">Required attribute.</span></span><br><br><span data-ttu-id="52120-112">Gibt den Namen des Abschnitts oder Abschnittsgruppe zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="52120-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="52120-113">Übergeordnetes Element</span><span class="sxs-lookup"><span data-stu-id="52120-113">Parent element</span></span>

|     | <span data-ttu-id="52120-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="52120-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="52120-115">**\<ConfigSections >** Element</span><span class="sxs-lookup"><span data-stu-id="52120-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="52120-116">Enthält die Konfiguration im Abschnitt und Namespacedeklarationen.</span><span class="sxs-lookup"><span data-stu-id="52120-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="52120-117">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="52120-117">Child elements</span></span>

<span data-ttu-id="52120-118">Keine</span><span class="sxs-lookup"><span data-stu-id="52120-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="52120-119">Hinweise</span><span class="sxs-lookup"><span data-stu-id="52120-119">Remarks</span></span>

<span data-ttu-id="52120-120">Die  **\<deaktivieren >** Element entfernt alle Abschnitte und Abschnittsgruppen aus der Anwendung, die weiter oben in der aktuellen Konfigurationsdatei oder auf einer höheren Ebene in der Hierarchie der Konfigurationsdatei definiert wurden.</span><span class="sxs-lookup"><span data-stu-id="52120-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="52120-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="52120-121">Example</span></span>

<span data-ttu-id="52120-122">In diesem Beispiel definiert eine Computerkonfigurationsdatei und einer Anwendungskonfigurationsdatei und zeigt, wie die  **\<deaktivieren >** Element in einer Anwendungskonfigurationsdatei gelöscht zuvor definierten Abschnitte der die Computerkonfigurationsdatei.</span><span class="sxs-lookup"><span data-stu-id="52120-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="52120-123">Der folgende Konfigurationscode Datei Computer deklariert zwei Abschnitte  **\<SampleSection >** und  **\<AnotherSampleSection >**, die vor der Anwendung gelesen werden die Konfigurationsdatei:</span><span class="sxs-lookup"><span data-stu-id="52120-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="52120-124">Der folgende Code für eine Anwendungskonfigurationsdatei löscht alle zuvor deklarierten Abschnitte.</span><span class="sxs-lookup"><span data-stu-id="52120-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="52120-125">Die Anwendung kann nicht verwendet oder Abrufen von Einstellungen in den Abschnitten, die in der Computerkonfigurationsdatei deklariert wurden.</span><span class="sxs-lookup"><span data-stu-id="52120-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="52120-126">Es können jedoch Einstellungen von  **\<AnotherSection >** , da es nach geht die  **\<deaktivieren >** Element.</span><span class="sxs-lookup"><span data-stu-id="52120-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="52120-127">Konfigurationsdatei</span><span class="sxs-lookup"><span data-stu-id="52120-127">Configuration file</span></span>

<span data-ttu-id="52120-128">Dieses Element kann in der Anwendungskonfigurationsdatei Computerkonfigurationsdatei verwendet werden (*"Machine.config"*), und *"Web.config"* Dateien, die nicht auf Anwendungsebene Verzeichnis sind.</span><span class="sxs-lookup"><span data-stu-id="52120-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="52120-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="52120-129">See also</span></span>

[<span data-ttu-id="52120-130">Konfigurationsdateischema für .NET Framework</span><span class="sxs-lookup"><span data-stu-id="52120-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)