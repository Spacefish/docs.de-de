---
title: 'Gewusst wie: Binden eines Windows Forms-Steuerelements an einen Typ mithilfe des Designers'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215a69a47b0588e45fcc28202dce4c6210b1dfe6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Gewusst wie: Binden eines Windows Forms-Steuerelements an einen Typ mithilfe des Designers
Beim Erstellen von Steuerelementen, die mit Daten interagieren, ist es manchmal erforderlich, ein Steuerelement an einen Typ statt an ein Objekt zu binden. Sie müssen normalerweise ein Steuerelement zur Entwurfszeit an einen Typ binden, wenn Daten möglicherweise nicht verfügbar sind, aber die datengebundenen Steuerelemente dennoch Daten von der öffentlichen Schnittstelle eines Typs anzeigen sollen. Die folgenden Verfahren wird gezeigt, wie zum Erstellen eines neuen <xref:System.Windows.Forms.BindingSource> also an einen Typ gebunden, und klicken Sie dann eine der Eigenschaften des Typs binden der <xref:System.Windows.Forms.TextBox.Text%2A> Eigenschaft eine <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>So binden Sie die BindingSource an einen Typen  
  
1.  Erstellen Sie ein Windows Forms-Projekt.  
  
     Weitere Informationen finden Sie unter [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  In **Entwurf** anzuzeigen, ziehen Sie eine <xref:System.Windows.Forms.BindingSource> -Komponente auf das Formular.  
  
3.  In der **Eigenschaften** Fenster, klicken Sie auf den Pfeil für den <xref:System.Windows.Forms.BindingSource.DataSource%2A> Eigenschaft.  
  
4.  Klicken Sie im **DataSource-UI-Typ-Editor** auf **Projektdatenquelle hinzufügen**.  
  
5.  Wählen Sie auf der Seite **Datenquellentyp auswählen** die Option **Objekt** aus, und klicken Sie dann auf **Weiter**.  
  
6.  Wählen Sie den Typ aus, an den gebunden werden soll:  
  
    -   Wenn sich der Typ, den Sie binden möchten, im aktuellen Projekt befindet oder die Assembly, die den Typ enthält, bereits als Verweis hinzugefügt ist, müssen Sie die Knoten erweitern, um den gewünschten Typ zu suchen. Wählen Sie ihn anschließend aus.  
  
         - oder -   
  
    -   Wenn sich der Typ, den Sie binden möchten, in einer anderen Assembly befindet, die derzeit nicht in der Liste der Verweise erscheint, klicken Sie auf **Verweis hinzufügen** und anschließend auf die Registerkarte **Projekte**. Wählen Sie das Projekt aus, das das gewünschte Geschäftsobjekt enthält, und klicken Sie auf **OK**. Dieses Projekt erscheint in der Liste der Assemblys. Dadurch können Sie die Knoten erweitern, um den gewünschten Typ zu suchen und ihn anschließend auszuwählen.  
  
        > [!NOTE]
        >  Deaktivieren Sie das Dialogfeld **Assemblys ausblenden, die mit „Microsoft“ oder „System“ beginnen**, wenn Sie an einen Typen in einem Framework oder einer Microsoft-Assembly binden möchten.  
  
7.  Klicken Sie auf **Weiter** und anschließend auf **Fertig stellen**.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>So binden Sie das Steuerelement an die BindingSource  
  
1.  Fügen Sie dem Formular eine <xref:System.Windows.Forms.TextBox> hinzu.  
  
2.  Erweitern Sie im Fenster **Eigenschaften** den Knoten **(DataBindings)**.  
  
3.  Klicken Sie auf den Pfeil neben der <xref:System.Windows.Forms.TextBox.Text%2A> Eigenschaft.  
  
4.  In der **DataSource UI-Typ-Editor**, erweitern Sie den Knoten für die <xref:System.Windows.Forms.BindingSource> zuvor hinzugefügt, und wählen Sie die Eigenschaft des gebundenen Typs, die Sie binden möchten die <xref:System.Windows.Forms.TextBox.Text%2A> Eigenschaft von der <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Siehe auch  
 [BindingSource-Komponente](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Vorgehensweise: Binden eines Windows Forms-Steuerelements an einen Typ](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Binden von Steuerelementen an Daten in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
