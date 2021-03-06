---
title: Auftragsverarbeitung mit Richtlinie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aaab8fca4693f6b253d48f066e644cc76637241
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2017
---
# <a name="order-processing-with-policy"></a>Auftragsverarbeitung mit Richtlinie
Das Beispiel Auftragsverarbeitungsrichtlinie veranschaulicht einige der in [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] von Windows Workflow Foundation (WF) eingeführten Schlüsselfeatures. Die folgende Funktionalität ist für das WF-Regelmodul neu:  
  
-   Unterstützung für Operatorüberladung.  
  
-   Unterstützung für den `new`-Operator, mit dem die Benutzer neue Objekte und Arrays von WF-Regeln erstellen können.  
  
-   Unterstützung von Erweiterungsmethoden, um die Benutzerfreundlichkeit beim Aufrufen der Erweiterungsmethoden von WF-Regeln mit den C#-Codierungsstilen kompatibel zu machen.  
  
> [!NOTE]
>  Für dieses Beispiel ist es erforderlich, dass [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] für die Erstellung und Ausführung installiert ist. [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ist erforderlich, um die Projekt- und Projektmappendateien zu öffnen.  
  
 Das Beispiel veranschaulicht ein `OrderProcessingPolicy`-Projekt, in dem eine Kundenbestellung eingegeben wird, die aus einer nummerierten Liste mit verfügbaren Elementen und einer Postleitzahl besteht. Die Bestellung wird erfolgreich verarbeitet, wenn beide Einträge richtig sind. Andernfalls erstellt die Richtlinie Fehlerobjekte, wobei ein überladener `+`-Operator sowie eine vordefinierte Erweiterungsmethode verwendet werden, um den Benutzer über die Fehler zu informieren.  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Erweiterungsmethoden [c#], finden Sie unter [c# Version 3.0-Spezifikation](http://go.microsoft.com/fwlink/?LinkId=95402).  
  
 Das Beispiel besteht aus den folgenden Projekten:  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` ist eine Klassenbibliothek, mit der die `OrderError`-Klasse und die `OrderErrorCollection`-Klasse definiert werden. Eine `OrderError`-Instanz wird erstellt, wenn eine ungültige Eingabe gemacht wird. Die Bibliothek bietet auch eine Erweiterungsmethode in der `OrderErrorCollection`-Klasse, mit der die `ErrorText`-Eigenschaft für alle `OrderError`-Objekte in der `OrderErrorCollection` ausgegeben wird.  
  
-   `OrderProcessingPolicy`  
  
     Das `OrderProcessingPolicy`-Projekt ist eine WF-Konsolenanwendung, die eine einzelne `PolicyFromFile`-Aktivität definiert. Die Aktivität weist folgende Regeln auf:  
  
    -   `invalidItemNum`  
  
         Diese Regel überprüft, dass die Artikelnummer zwischen 1 und 6 liegt. Wenn die Artikelnummer innerhalb des gültigen Bereichs liegt, führt die Regel keine Aktion aus (mit Ausnahme des Druckens auf der Konsole). Wenn die Artikelnummer nicht zwischen 1 und 6 liegt, geht die `invalidItemNum`-Regel wie folgt vor:  
  
        1.  Sie erstellt ein neues `OrderError`-Objekt und übergibt ihm die eingegebene Artikelnummer. Außerdem legt sie die `ErrorText`-Eigenschaft und die `CustomerName`-Eigenschaft für das Objekt fest.  
  
        2.  Sie erstellt ein `invalidItemNumErrorCollection`-Objekt.  
  
        3.  Sie fügt die neu erstellte `OrderError`-Instanz der `invalidItemNumErrorCollection` hinzu.  
  
         Dies weist auf die Unterstützung des `new`-Operators hin, mit dem Objekte in Regeln instanziiert werden können.  
  
    -   `invalidZip`  
  
         Diese Regel überprüft, ob die Postleitzahl 5 Ziffern hat und im Bereich 600 bis 99998 liegt. Wenn die Postleitzahl innerhalb des gültigen Bereichs liegt, führt die Regel keine Aktion aus (mit Ausnahme der Ausgabe auf der Konsole). Falls die Postleitzahl weniger als 5 Stellen aufweist oder nicht im Bereich 00600 bis 99998 liegt, geht die `invalidZip`-Regel wie folgt vor:  
  
        1.  Sie erstellt ein `OrderError`-Objekt und übergibt ihm die eingegebene Postleitzahl. Außerdem legt sie die `ErrorText`-Eigenschaft und die `CustomerName`-Eigenschaft für das Objekt fest.  
  
        2.  Sie erstellt ein `invalidZipCodeErrorCollection`-Objekt.  
  
        3.  Sie fügt die neu erstellte `OrderError`-Instanz der neu erstellten `invalidZipCodeErrorCollection` hinzu.  
  
         Diese Regel veranschaulicht die Unterstützung des `new`-Operators, mit dem Objekte in Regeln instanziiert werden können.  
  
    -   `displayErrors`  
  
         Bei dieser Regel wird überprüft, ob von den vorherigen beiden Regeln in den beiden `OrderErrorCollection`-Objekten `invalidItemNumErrorCollection` und `invalidIZipCodeErrorCollection` Fehler hinzugefügt wurden. Wenn es Fehler (entweder die `invalidItemNumErrorCollection` oder die `invalidZipCodeErrorCollection` ist nicht `null`) gegeben hat, geht die Regel wie folgt vor:  
  
        1.  Ruft den überladenen `+` -Operator zum Kopieren des Inhalts der `invalidItemNumErrorCollection` und `invalidZipCodeErrorCollection` auf eine `invalidOrdersCollection``OrderErrorCollection` Instanz.  
  
        2.  Sie ruft die `PrintOrderErrors`-Erweiterungsmethode für die `invalidOrdersCollection` auf und gibt die `ErrorText`-Eigenschaft für alle `orderError`-Objekte in der `invalidOrdersCollection` aus.  
  
 Der überladene `+`-Operator der `OrderErrorCollection` wird in der `OrderErrorCollection`-Klasse im `OrderErrorLibrary`-Projekt definiert. Er verfügt über zwei `OrderErrorCollection`-Objekte und kombiniert diese in einem `OrderErrorCollection`-Objekt.  
  
 Die `PrintOrderErrors`-Erweiterungsmethode wird auch im `OrderErrorLibrary`-Projekt definiert. Erweiterungsmethoden sind ein neues C#-Feature, mit dem Entwickler dem öffentlichen Vertrag eines vorhandenen CLR-Typs neue Methoden hinzufügen können, ohne davon eine Klasse ableiten oder den ursprünglichen Typ neu kompilieren zu müssen.  
  
 Beim Ausführen eines Beispiels werden Sie zur Eingabe eines Namens, der Artikelnummer des zu erwerbenden Artikels und einer Postleitzahl aufgefordert. Diese Informationen werden dann von den in der Richtlinienaktivität definierten Regeln überprüft. Im Folgenden finden Sie eine Beispielausgabe des Programms.  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>So können Sie das Beispiel einrichten, erstellen und ausführen  
  
1.  Öffnen Sie die Projektdatei OrderProcessingPolicy.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Es gibt zwei verschiedene Projekte in der Projektmappe: `OrderErrorLibrary` und `OrderProcessingPolicy`. Das `OrderProcessingPolicy`-Projekt verwendet in der `OrderErrorLibrary` definierte Klassen und Methoden.  
  
3.  Erstellen Sie alle Projekte.  
  
4.  Klicken Sie auf **ausführen**.  
  
> [!IMPORTANT]
>  Die Beispiele sind möglicherweise bereits auf dem Computer installiert. Suchen Sie nach dem folgenden Verzeichnis (Standardverzeichnis), bevor Sie fortfahren:  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Wenn dieses Verzeichnis nicht vorhanden ist, rufen Sie [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) auf, um alle [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] - und [!INCLUDE[wf1](../../../../includes/wf1-md.md)] -Beispiele herunterzuladen. Dieses Beispiel befindet sich im folgenden Verzeichnis:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`