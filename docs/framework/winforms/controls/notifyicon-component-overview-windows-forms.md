---
title: Visão geral do componente NotifyIcon (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
ms.openlocfilehash: 5d77099eeb1ef33f3b9e65bd99d4e22e38c3ec38
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087193"
---
# <a name="notifyicon-component-overview-windows-forms"></a>Visão geral do componente NotifyIcon (Windows Forms)

Os formulários do Windows <xref:System.Windows.Forms.NotifyIcon> componente normalmente é usado para exibir ícones para processos que são executados em segundo plano e não mostram que um usuário de interface grande parte do tempo. Por exemplo, um programa de proteção contra vírus que pode ser acessado clicando em um ícone na área de notificação de status da barra de tarefas.

## <a name="key-properties-of-notifyicons"></a>Propriedades chave do NotifyIcons

Cada <xref:System.Windows.Forms.NotifyIcon> componente exibe um único ícone na área de status. Se você tem três processos em segundo plano e desejar exibir um ícone para cada um, você deve adicionar três <xref:System.Windows.Forms.NotifyIcon> componentes para o formulário. As propriedades da chave de <xref:System.Windows.Forms.NotifyIcon> componente estão <xref:System.Windows.Forms.NotifyIcon.Icon%2A> e <xref:System.Windows.Forms.NotifyIcon.Visible%2A>. O <xref:System.Windows.Forms.NotifyIcon.Icon%2A> propriedade define o ícone que aparece na área de status. Para que o ícone apareça, a <xref:System.Windows.Forms.NotifyIcon.Visible%2A> propriedade deve ser definida como `true`.

## <a name="notifyicons-options"></a>Opções do NotifyIcons

Você pode associar dicas de balão, menus de atalho e dicas de ferramenta com um <xref:System.Windows.Forms.NotifyIcon> para auxiliar o usuário.

Você pode exibir dicas de balão para um <xref:System.Windows.Forms.NotifyIcon> chamando o <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> método especificando o intervalo de tempo você deseja exibir a dica de balão. Você também pode especificar o texto, ícone e título da dica de balão com o <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> e <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectivamente. <xref:System.Windows.Forms.NotifyIcon> componentes também podem ter associadas dicas de ferramentas e menus de atalho. Para mais informação, consulte [Visão geral do componente ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) e [Visão geral do componente ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.NotifyIcon>
- [Componente NotifyIcon](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)