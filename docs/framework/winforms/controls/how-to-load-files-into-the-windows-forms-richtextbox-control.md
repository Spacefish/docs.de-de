---
title: 'Gewusst wie: Laden von Dateien in das RichTextBox-Steuerelement von Windows Forms'
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
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0e2aec42fa3656b64140134efa27fe8e940e1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Gewusst wie: Laden von Dateien in das RichTextBox-Steuerelement von Windows Forms
Das <xref:System.Windows.Forms.RichTextBox> -Steuerelement von Windows Forms kann eine Nur-Text-, Unicode-Nur-Text- oder Rich-Text-Format-Datei (RTF) anzeigen. Rufen Sie dazu die <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> -Methode auf. Sie können die <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> -Methode auch zum Laden von Daten aus einem Stream verwenden. Weitere Informationen finden Sie unter <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a>So laden Sie eine Datei in das RichTextBox-Steuerelement  
  
1.  Bestimmen Sie den Pfad der Datei, die geöffnet werden soll, mithilfe der <xref:System.Windows.Forms.OpenFileDialog> -Komponente. Eine Übersicht finden Sie unter [Übersicht über die OpenFileDialog-Komponente](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).  
  
2.  Rufen Sie die <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> -Methode des <xref:System.Windows.Forms.RichTextBox> -Steuerelements auf und geben Sie dabei die zu ladende Datei und optional einen Dateityp an. Im folgenden Beispiel stammt die zu ladende Datei aus der <xref:System.Windows.Forms.OpenFileDialog> -Eigenschaft der <xref:System.Windows.Forms.FileDialog.FileName%2A> Komponente. Wenn Sie die Methode mit einem Dateinamen als einziges Argument aufrufen, wird RTF als Dateityp angenommen. Rufen Sie zum Angeben eines anderen Dateityps die Methode mit dem Wert der <xref:System.Windows.Forms.RichTextBoxStreamType> -Enumeration als zweites Argument auf.  
  
     Im folgenden Beispiel wird die <xref:System.Windows.Forms.OpenFileDialog> -Komponente angezeigt, wenn auf eine Schaltfläche geklickt wird. Die ausgewählte Datei wird anschließend geöffnet und im <xref:System.Windows.Forms.RichTextBox> -Steuerelement angezeigt. In diesem Beispiel wird angenommen, dass eine Form eine Schaltfläche`btnOpenFile`enthält.  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Fügen Sie den folgenden Code in den Konstruktor der Form ein, um den Ereignishandler zu registrieren.  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  Die Assembly benötigt zum Ausführen dieses Prozesses möglicherweise eine von der <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>-Klasse gewährte Berechtigungsebene. Wenn Sie in einem teilweise vertrauenswürdigen Kontext arbeiten, kann der Vorgang aufgrund fehlender Berechtigungen eine Ausnahme auslösen. Weitere Informationen finden Sie unter [Grundlagen der Codezugriffssicherheit](../../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox-Steuerelement](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms-Steuerelemente](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
