---
title: "Como adicionar e remover nós com o componente TreeView dos Windows Forms usando o designer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f6295f915e9204e9996d8902b07a3dfc4c5c2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>Como adicionar e remover nós com o componente TreeView dos Windows Forms usando o designer
Como o Windows Forms <xref:System.Windows.Forms.TreeView> controle exibe nós de uma maneira hierárquica, ao adicionar um nó, você deve prestar atenção ao nó pai.  
  
 O procedimento a seguir requer um **aplicativo do Windows** projeto com um formulário que contém um <xref:System.Windows.Forms.TreeView> controle. Para obter informações sobre como configurar um projeto desse tipo, consulte [Como Criar um Projeto de Aplicativo do Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) e [Como Adicionar Controles ao Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a>Para adicionar ou remover nós no designer  
  
1.  Selecione o <xref:System.Windows.Forms.TreeView> controle.  
  
2.  No **propriedades** janela, clique no **reticências** (![de tela de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) próximo ao o <xref:System.Windows.Forms.TreeView.Nodes%2A> propriedade.  
  
     O **Editor TreeNode** é exibido.  
  
3.  Para adicionar nós, deve existir um nó raiz; se não existir, primeiro adicione uma raiz clicando no botão **Adicionar Raiz**. Em seguida, adicione nós filho, selecionando a raiz ou qualquer outro nó e clicando no botão **Adicionar Filho**.  
  
4.  Para excluir nós, selecione o nó a ser excluído e clique no botão **Excluir**.  
  
## <a name="see-also"></a>Consulte também  
 [Controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [Visão geral do controle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Como definir ícones para o controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [Como iterar em todos os nós de um controle TreeView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Como determinar qual nó TreeView foi clicado](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Como adicionar informações personalizadas a um controle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)