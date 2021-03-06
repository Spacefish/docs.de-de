---
title: 'Gewusst wie: Bereitstellen von Hilfe in einer Windows-Anwendung'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f407f1c17c67ec99f4499b89c49932a4ba6d32c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Gewusst wie: Bereitstellen von Hilfe in einer Windows-Anwendung
Können Sie von der <xref:System.Windows.Forms.HelpProvider> Komponente Hilfethemen in einer Hilfedatei bestimmten Steuerelementen in Windows Forms zuzuordnen. Die Hilfedatei kann entweder im Format HTML oder HTMLHelp 1.x oder höher vorliegen.  
  
> [!NOTE]
>  Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü **Extras** auf **Einstellungen importieren und exportieren** , um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Anpassen der Entwicklungseinstellungen in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-provide-help"></a>So wird die Hilfe verfügbar  
  
1.  Aus der **Toolbox**, ziehen Sie eine <xref:System.Windows.Forms.HelpProvider> -Komponente in Ihr Formular.  
  
     Die Komponente befindet sich anschließend auf der Taskleiste unten im Windows Forms-Designer.  
  
2.  In der **Eigenschaften** legen die <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> -Eigenschaft auf die CHM, col- oder HTML-Hilfedatei.  
  
3.  Wählen Sie ein anderes Steuerelement, Sie haben auf dem Formular, und in, der **Eigenschaften** legen die <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> Eigenschaft.  
  
     Dies ist die Zeichenfolge, die durch Übergeben der <xref:System.Windows.Forms.HelpProvider> -Komponente in der Hilfedatei, die die entsprechenden Hilfethema aufzurufen.  
  
4.  In der **Eigenschaften** legen die <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> Eigenschaft auf den Wert der <xref:System.Windows.Forms.HelpNavigator> Enumeration.  
  
     Dies bestimmt die Art, wie die **HelpKeyword**-Eigenschaft an das Hilfesystem übergeben wird. In der folgenden Tabelle werden die möglichen Einstellungen und ihre Beschreibungen aufgeführt.  
  
    |Membername|Beschreibung|  
    |-----------------|-----------------|  
    |AssociateIndex|Gibt an, dass der Index für ein Thema in der angegebenen URL ausgeführt wurde.|  
    |Find|Gibt an, dass die Suchseite der angegebenen URL angezeigt wird.|  
    |Index|Gibt an, dass der Index der angegebenen URL angezeigt wird.|  
    |KeywordIndex|Gibt ein Schlüsselwort an, nach dem gesucht wird, und die Aktion, die in der angegebenen URL vorzunehmen ist.|  
    |TableOfContents|Gibt an, dass das Inhaltsverzeichnis der HTML 1.0-Hilfedatei angezeigt wird.|  
    |Topic|Gibt an, dass das Thema angezeigt wird, auf das durch die angegebene URL verwiesen wird.|  
  
 Zur Laufzeit durch Drücken von F1 Wenn das Steuerelement – für die Sie festgelegt haben die **HelpKeyword** und **HelpNavigator** Eigenschaften – hat den Fokus öffnet die Hilfedatei, die Sie zugeordnet sind, <xref:System.Windows.Forms.HelpProvider> Komponente.  
  
 Momentan unterstützt die **HelpNamespace**-Eigenschaft Hilfedateien in folgenden drei Formaten: HTMLHelp 1.x, HTMLHelp 2.0 und HTML. Dies bedeutet, dass Sie die **HelpNamespace**-Eigenschaft auf eine http://-Adresse (z. B. eine Webseite) festlegen können. Daraufhin wird im Standardbrowser die Webseite mit der Zeichenfolge geöffnet, die in der als Anker verwendeten **HelpKeyword**-Eigenschaft angegeben ist. Der Anker wird verwendet, um zu einem bestimmten Teil einer HTML-Seite zu springen.  
  
> [!IMPORTANT]
>  Überprüfen Sie alle von einem Client gesendeten Informationen sorgfältig, bevor Sie diese in der Anwendung verwenden. Böswillige Benutzer könnten versuchen, ausführbare Skripts, SQL-Anweisungen oder anderen Code zu senden oder einzuschleusen. Bevor Sie die Eingabe eines Benutzers anzeigen, diese in einer Datenbank speichern oder damit arbeiten, müssen Sie sicherstellen, dass diese keine potenziell unsicheren Informationen enthält. Ein sehr gebräuchlicher Weg zur Überprüfung der von einem Benutzer übermittelten Eingaben ist die Verwendung eines regulären Ausdrucks, um nach Schlüsselwörtern wie SCRIPT zu suchen.  
  
 Sie können auch die <xref:System.Windows.Forms.HelpProvider> Komponente zum Anzeigen der kontextbezogenen Hilfe, auch wenn Sie diese so konfiguriert, dass die Hilfedateien für die Steuerelemente in Windows Forms angezeigt haben. Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen der kontextbezogenen Hilfe](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Anzeigen der kontextbezogenen Hilfe](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [Benutzerführung mithilfe von QuickInfos](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Integrieren von Benutzerhilfe in Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
