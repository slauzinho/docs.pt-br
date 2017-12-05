---
title: "Como habilitar operações arrastar e soltar com o controle RichTextBox dos Windows Forms"
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
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 91739643aaa2d7fe3ea302d0d35edabbae0ab14f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Como habilitar operações arrastar e soltar com o controle RichTextBox dos Windows Forms
Operações de arrastar e soltar com o Windows Forms <xref:System.Windows.Forms.RichTextBox> controle são feitos pelo tratamento de <xref:System.Windows.Forms.RichTextBox.DragEnter> e <xref:System.Windows.Forms.RichTextBox.DragDrop> eventos. Portanto, operações de arrastar e soltar são extremamente simples com o <xref:System.Windows.Forms.RichTextBox> controle.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Habilitar operações de arrastar em um controle RichTextBox  
  
1.  Definir o <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> propriedade do <xref:System.Windows.Forms.RichTextBox> controle `true`.  
  
2.  Escrever código no manipulador de eventos do <xref:System.Windows.Forms.RichTextBox.DragEnter> evento. Use uma instrução `if` para garantir que os dados que são arrastados pertencem a um tipo aceitável (neste caso, texto). O <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> propriedade pode ser definida como qualquer valor da <xref:System.Windows.Forms.DragDropEffects> enumeração.  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))   
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3.  Escreva código para manipular o <xref:System.Windows.Forms.RichTextBox.DragDrop> evento. Use o <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> método para recuperar os dados que está sendo arrastados.  
  
     No exemplo a seguir, o código define o <xref:System.Windows.Forms.RichTextBox.Text%2A> propriedade o <xref:System.Windows.Forms.RichTextBox> controlar igual aos dados que está sendo arrastados. Se já houver texto no <xref:System.Windows.Forms.RichTextBox> controle, o texto arrastado é inserido no ponto de inserção.  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _   
       ByVal e As System.Windows.Forms.DragEventArgs) _   
       Handles RichTextBox1.DragDrop  
       Dim i As Int16   
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,   
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +   
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());   
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] e [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew   
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Testar a funcionalidade do tipo "arrastar e soltar" no seu aplicativo  
  
1.  Salve e compile o aplicativo. Enquanto estiver em execução, execute o WordPad.  
  
     O WordPad é um editor de texto instalado pelo Windows que permite realizar operações do tipo "arrastar e soltar". Ele pode ser acessado clicando no botão **Iniciar**, selecionando **Executar**, digitando `WordPad` na caixa de texto da caixa de diálogo **Executar** e clicando em **OK**.  
  
2.  Após abrir o WordPad, digite uma cadeia de texto nele. Usando o mouse, selecione o texto e arraste o texto selecionado para o <xref:System.Windows.Forms.RichTextBox> controle no aplicativo do Windows.  
  
     Observe que, quando você apontar o mouse na <xref:System.Windows.Forms.RichTextBox> controle (e, consequentemente, gera o <xref:System.Windows.Forms.RichTextBox.DragEnter> evento), o ponteiro do mouse muda e você pode soltar o texto selecionado para o <xref:System.Windows.Forms.RichTextBox> controle.  
  
     Quando você solta o botão do mouse, o texto selecionado é descartado (isto é, o <xref:System.Windows.Forms.RichTextBox.DragDrop> é gerado) e é inserido dentro a <xref:System.Windows.Forms.RichTextBox> controle.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.RichTextBox>  
 [Como Executar Operações de do Tipo "Arrastar e Soltar" entre Aplicativos](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 [Controle RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Controles a serem usados nos Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)