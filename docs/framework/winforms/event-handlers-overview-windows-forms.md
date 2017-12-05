---
title: "Visão geral de manipuladores de eventos (Windows Forms)"
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
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a>Visão geral de manipuladores de eventos (Windows Forms)
Um manipulador de eventos é um método que está associado a um evento. Quando o evento é gerado, o código no manipulador de eventos é executado. Cada manipulador de eventos fornece dois parâmetros que permitem manipular o evento corretamente. O exemplo a seguir mostra um manipulador de eventos para um <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> eventos.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 No primeiro parâmetro, `sender`, fornece uma referência ao objeto que gerou o evento. No exemplo acima, o segundo parâmetro, `e`, passa um objeto específico para o evento que está sendo manipulado. Consultando as propriedades do objeto (e, às vezes, seus métodos), é possível obter informações como o local do mouse para eventos de mouse ou dados que estão sendo transferidos em eventos do tipo "arrastar e soltar".  
  
 Normalmente, cada evento produz um manipulador de eventos com um tipo de objeto de evento diferente para o segundo parâmetro. Alguns manipuladores de eventos, como aquelas para o <xref:System.Windows.Forms.Control.MouseDown> e <xref:System.Windows.Forms.Control.MouseUp> eventos, têm o mesmo tipo de objeto para o segundo parâmetro. Para esses tipos de eventos, você pode usar o mesmo manipulador de eventos para manipular ambos os eventos.  
  
 Você também pode usar o mesmo manipulador de eventos para manipular o mesmo evento em controles diferentes. Por exemplo, se você tiver um grupo de <xref:System.Windows.Forms.RadioButton> controles em um formulário, você pode criar um único manipulador de eventos para o <xref:System.Windows.Forms.Control.Click> eventos e ter cada controle <xref:System.Windows.Forms.Control.Click> evento associado ao manipulador de eventos único. Para obter mais informações, consulte [Como conectar vários eventos a um único manipulador de eventos nos Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Consulte também  
 [Criando manipuladores de eventos no Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Visão geral de eventos](../../../docs/framework/winforms/events-overview-windows-forms.md)