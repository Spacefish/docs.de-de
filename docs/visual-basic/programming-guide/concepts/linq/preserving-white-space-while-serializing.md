---
title: "Beibehalten von Leerzeichen während Serializing2"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 93cfc1c14d75078170d6e1bbb3fc4ad72f47a206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-serializing"></a>Beibehalten von Leerzeichen beim Serialisieren
In diesem Thema wird beschrieben, wie Sie das Leerraumverhalten beim Serialisieren von XML-Strukturen steuern können.  
  
 Es kommt häufig vor, dass XML mit Einzügen gelesen und dann im Arbeitsspeicher eine XML-Struktur ohne Leerraumtextknoten erstellt wird (Leerräume bleiben also nicht erhalten). Anschließend wird der XML-Code geändert und dann mit Einzügen gespeichert. Wenn Sie den XML-Code mit Formatierung serialisieren, bleibt nur signifikanter Leerraum in der XML-Struktur erhalten. Dies ist das Standardverhalten bei [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Aber auch dieses Szenario ist häufig anzutreffen: XML-Code, der bereits absichtlich mit Einzügen versehen wurde, wird gelesen und geändert. Sie möchten nicht, dass diese Einzüge irgendwie geändert werden. In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] können Sie dies erreichen, indem Sie den Leerraum beim Laden oder Analysieren des XML-Codes beibehalten und dann beim Serialisieren des XML-Codes die Formatierung deaktivieren.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Leerraumverhalten von Methoden, die XML-Strukturen serialisieren  
 Die folgenden Methoden in den Klassen <xref:System.Xml.Linq.XElement> und <xref:System.Xml.Linq.XDocument> serialisieren eine XML-Struktur. Sie können XML-Strukturen in eine Datei, in einen <xref:System.IO.TextReader> oder in einen <xref:System.Xml.XmlReader> serialisieren. Die `ToString`-Methode nimmt eine Serialisierung in eine Zeichenfolge vor.  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 Wenn die Methode nicht <xref:System.Xml.Linq.SaveOptions> als Argument akzeptiert, formatiert die Methode den serialisierten XML-Code, indem sie ihn mit Einzügen versieht. In diesem Fall wird der gesamte nicht signifikante Leerraum in der XML-Struktur verworfen.  
  
 Wenn die Methode <xref:System.Xml.Linq.SaveOptions> als Argument akzeptiert, können Sie angeben, dass der serialisierte XML-Code nicht formatiert (eingerückt) werden soll. In diesem Fall wird der gesamte Leerraum in der XML-Struktur beibehalten.  
  
## <a name="see-also"></a>Siehe auch  
 [Serialisieren von XML-Strukturen (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
