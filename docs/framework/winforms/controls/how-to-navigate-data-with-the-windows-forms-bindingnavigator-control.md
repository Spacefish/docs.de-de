---
title: 'Gewusst wie: Datennavigation mithilfe des BindingNavigator-Steuerelements in Windows Forms'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08b9fb555966cf8459646a12da69c6db3361f0b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Gewusst wie: Datennavigation mithilfe des BindingNavigator-Steuerelements in Windows Forms
Die Einführung des <xref:System.Windows.Forms.BindingNavigator>-Steuerelements in Windows Forms ermöglicht es Entwicklern, Endbenutzern eine einfache Benutzeroberfläche für die Datennavigation und -bearbeitung auf den Formularen bereitzustellen, die sie erstellen.  
  
 Das <xref:System.Windows.Forms.BindingNavigator>-Steuerelement ist ein <xref:System.Windows.Forms.ToolStrip>-Steuerelement mit Schaltflächen, die für die Navigation zum ersten, letzten, nächsten und vorherigen Datensatz in einem Dataset vorkonfiguriert sind, sowie mit Schaltflächen zum Hinzufügen und Löschen von Datensätzen. Schaltflächen lassen sich ganz einfach zu dem <xref:System.Windows.Forms.BindingNavigator>-Steuerelement hinzufügen, da es ein <xref:System.Windows.Forms.ToolStrip>-Steuerelement ist.  Siehe auch [Vorgehensweise: Hinzufügen der Schaltflächen für das Laden, Speichern und Abbrechen zum BindingNavigator-Steuerelement in Windows Forms](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).  
  
 Für jede Schaltfläche im <xref:System.Windows.Forms.BindingNavigator>-Steuerelement gibt es einen entsprechenden Member der <xref:System.Windows.Forms.BindingSource>-Komponente, die dieselbe Funktionalität programmgesteuert bereitstellt. Beispielsweise entspricht die <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A>-Schaltfläche der <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>-Methode der <xref:System.Windows.Forms.BindingSource>-Komponente, die <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A>-Schaltfläche der <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>-Methode usw. Demzufolge ist das Aktivieren des <xref:System.Windows.Forms.BindingNavigator>-Steuerelements für die Navigation zwischen Datensätzen ebenso einfach wie das Festlegen seiner <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>-Eigenschaft auf die entsprechende <xref:System.Windows.Forms.BindingSource>-Komponente auf dem Formular.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>So richten Sie das BindingNavigator-Steuerelement ein  
  
1.  Fügen Sie eine <xref:System.Windows.Forms.BindingSource>-Komponente namens `bindingSource1` und zwei <xref:System.Windows.Forms.TextBox>-Steuerelemente namens `textBox1` und `textBox2` hinzu.  
  
2.  Binden Sie `bindingSource1` an Daten und die TextBox-Steuerelemente an `bindingSource1`. Fügen Sie zu diesem Zweck den folgenden Code in Ihr Formular ein, und rufen Sie `LoadData` aus dem Konstruktor des Formulars oder der <xref:System.Windows.Forms.Form.Load>-Ereignisbehandlungsmethode heraus auf.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Fügen Sie Ihrem Formular ein <xref:System.Windows.Forms.BindingNavigator>-Steuerelement namens `bindingNavigator1` hinzu.  
  
4.  Legen Sie die <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>-Eigenschaft für `bindingNavigator1` auf `bindingSource1` fest. Dies ist mit dem Designer oder im Code möglich.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel ist das vollständige Beispiel für die zuvor aufgeführten Schritte.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Für dieses Beispiel benötigen Sie Folgendes:  
  
-   Verweise auf die Assemblys "System", "System.Data", "System.Drawing", "System.Windows.Forms" und "System.Xml".  
  
 Informationen zum Erstellen dieses Beispiels über die Befehlszeile für [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] oder [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] finden Sie unter [Erstellen von der Befehlszeile aus](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) oder [Erstellen über die Befehlszeile mit „csc.exe“](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Sie können dieses Beispiel auch in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] erstellen, indem Sie den Code in ein neues Projekt einfügen.  Siehe auch: [Vorgehensweise: Kompilieren und Ausführen eines vollständigen Windows Forms-Codebeispiels mit Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingNavigator-Steuerelement](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [ToolStrip-Steuerelement](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
