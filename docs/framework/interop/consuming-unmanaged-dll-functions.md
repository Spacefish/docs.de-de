---
title: Verwenden nicht verwalteter DLL-Funktionen
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- platform invoke, about platform invoke
- DLL functions, consuming unmanaged
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke
- DLL functions
ms.assetid: eca7606e-ebfb-4f47-b8d9-289903fdc045
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ec93728566d6aa16d4b9b15b171d79831cc0dbeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-unmanaged-dll-functions"></a>Verwenden nicht verwalteter DLL-Funktionen
Der Plattformaufruf ist ein Dienst, der es verwaltetem Code ermöglicht, nicht verwaltete Funktionen aufzurufen, die in DLLs (Dynamic Link Library) implementiert sind, z. B. die in der Win32-API enthaltenen Funktionen. Es sucht eine exportierte Funktion, ruft diese auf und marshallt ihre Argumente (ganze Zahlen, Zeichenfolgen, Arrays, Strukturen usw.) bei Bedarf über die Grenzen des dialogfähigen Betriebs hinaus. Weitere Informationen zu diesem Dienst finden Sie unter [Genauere Betrachtung von Plattformaufrufen](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243).  
  
 In diesem Abschnitt werden verschiedene Aufgaben eingeführt, die der Verarbeitung von nicht verwalteten DLL-Funktionen zugeordnet sind. Zusätzlich zu den folgenden Aufgaben sind allgemeine Überlegungen und ein Link enthalten, die weitere Informationen und Beispiele bieten.  
  
#### <a name="to-consume-exported-dll-functions"></a>So verarbeiten Sie exportierte DLL-Funktionen  
  
1.  [Identifizieren von Funktionen in DLLs](../../../docs/framework/interop/identifying-functions-in-dlls.md).  
  
     Sie müssen mindestens den Namen der Funktion und den Namen der DLL angeben, in der sie enthalten ist.  
  
2.  [Erstellen einer Klasse zum Halten von DLL-Funktionen](../../../docs/framework/interop/creating-a-class-to-hold-dll-functions.md).  
  
     Sie können eine bestehende Klasse verwenden, eine einzelne Klasse für jede nicht verwaltete Funktion erstellen oder eine Klasse erstellen, die einen Satz zusammengehöriger, nicht verwalteter Funktionen enthält.  
  
3.  [Erstellen von Prototypen in verwaltetem Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).  
  
     [Visual Basic] Verwenden Sie die **Declare**-Anweisung mit den Schlüsselwörtern **Function** und **Lib**. In seltenen Fällen können Sie **DllImportAttribute** mit den Schlüsselwörtern **Shared Function** verwenden. Diese Fälle werden weiter unten in diesem Abschnitt erläutert.  
  
     [C#] Verwenden Sie **DllImportAttribute**, um die DLL und die Funktion zu identifizieren. Kennzeichnen Sie die Methode mit den Modifizierern **static** und **extern**.  
  
     [C++] Verwenden Sie **DllImportAttribute**, um die DLL und die Funktion zu identifizieren. Kennzeichnen Sie die Wrappermethode oder Funktion mit **extern "C"**.  
  
4.  [Aufrufen einer DLL-Funktion](../../../docs/framework/interop/calling-a-dll-function.md).  
  
     Rufen Sie die Methode für Ihre verwaltete Klasse wie für jede andere verwaltete Methode auf. [Übergeben von Strukturen](../../../docs/framework/interop/passing-structures.md) und [Implementieren von Rückruffunktionen](../../../docs/framework/interop/callback-functions.md) sind spezielle Fälle.  
  
 Beispiele für die Vorgehensweise beim Erstellen von .NET-basierten Deklarationen, die mit dem Plattformaufruf verwendet werden können, finden Sie unter [Marshaling Data with Platform Invoke (Marshallen von Daten mit Plattformaufruf)](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).  
  
## <a name="a-closer-look-at-platform-invoke"></a>Genauere Betrachtung von Plattformaufrufen  
 Plattformaufrufe beruhen auf Metadaten, um exportierte Funktionen zu suchen und ihre Argumente zur Laufzeit zu marshallen. Die folgende Abbildung veranschaulicht diesen Prozess.  
  
 ![Plattformaufruf](../../../docs/framework/interop/media/pinvoke.gif "Pinvoke")  
Plattformaufruf für eine nicht verwaltete DLL-Funktion  
  
 Wenn der Plattformaufruf eine nicht verwaltete Funktion aufruft, werden die folgenden Aktionen nacheinander ausgeführt:  
  
1.  Suchen der DLL, die die Funktion enthält.  
  
2.  Laden der DLL in den Arbeitsspeicher.  
  
3.  Suchen der Adresse der Funktion im Arbeitsspeicher und Übertragen ihrer Argumente auf den Stapel, wobei die Daten bei Bedarf gemarshallt werden.  
  
    > [!NOTE]
    >  Das Suchen und Laden der DLL sowie das Suchen der Adresse der Funktion im Arbeitsspeicher erfolgen nur beim ersten Aufruf der Funktion.  
  
4.  Übertragen der Kontrolle an die nicht verwaltete Funktion.  
  
 Der Plattformaufruf löst Ausnahmen aus, die von der nicht verwalteten Funktion für den verwalteten Aufrufer generiert wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Interoperabilität mit nicht verwaltetem Code](../../../docs/framework/interop/index.md)  
 [Beispiele für Plattformaufrufe](../../../docs/framework/interop/platform-invoke-examples.md)  
 [Interop Marshaling (Interop-Marshalling)](../../../docs/framework/interop/interop-marshaling.md)  
 [Verwenden nicht verwalteter DLL-Funktionen](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
