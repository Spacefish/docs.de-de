---
title: "Geschützte Member"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c3aacd0f08641c01200f0b1791a78413a306590
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="protected-members"></a>Geschützte Member
Geschützte Member selbst bieten keine Erweiterungen können, sie jedoch Erweiterbarkeit durch Unterklassen leistungsfähiger. Sie können erweiterte Anpassungsoptionen verfügbar machen, ohne unnötig erschwert die wichtigsten öffentliche Schnittstelle verwendet werden.  
  
 Framework-Entwickler müssen mit geschützte Member vorsichtig sein, da der Namen "geschützt" auf "false" wie Sicherheit geben kann. Jeder Benutzer kann auf Unterklasse in einer unversiegelten Klasse und den Zugriff auf geschützte Member und also alle den gleichen defensive Codierungstechniken für öffentliche Member verwendet, die auf geschützte Member anwenden.  
  
 **✓ GGF.** mit geschützte Member für die erweiterte Anpassung.  
  
 **Führen Sie ✓** geschützte Member in nicht versiegelten Klassen als öffentlich für die Sicherheit, Dokumentation und Kompatibilität Analyse zu behandeln.  
  
 Jeder kann von einer Klasse erben und die geschützten Member zuzugreifen.  
  
 *Teilen © 2005, 2009 Microsoft Corporation. Alle Rechte vorbehalten.*  
  
 *Nachdruck mit Genehmigung von Pearson-Education, Inc. aus [Framework-Entwurfsrichtlinien: Konventionen, Idiome und Muster für Wiederverwendbaren .NET-Bibliotheken, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina und Brad Abrams veröffentlicht 22 Oktober 2008 durch Addison Wesley Professional als Teil der Microsoft Windows-Entwicklung Reihe.*  
  
## <a name="see-also"></a>Siehe auch  
 [Frameworkentwurfsrichtlinien](../../../docs/standard/design-guidelines/index.md)  
 [Entwerfen für Erweiterbarkeit](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
