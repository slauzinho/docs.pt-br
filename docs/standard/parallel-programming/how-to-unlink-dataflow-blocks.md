---
title: 'Como: Desvincular blocos de fluxo de dados'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc0f266169a2d82bb76355febd58b2268907fe97
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46540600"
---
# <a name="how-to-unlink-dataflow-blocks"></a>Como: Desvincular blocos de fluxo de dados
Este documento descreve como desvincular um bloco de fluxo de dados de destino de sua origem.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Exemplo  
 O exemplo a seguir cria três objetos <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, cada um chamando o método `TrySolution` para calcular um valor. Este exemplo exige apenas o resultado da primeira chamada a `TrySolution` para concluir.  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 Para receber o valor do primeiro objeto <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> concluído, esse exemplo define o método `ReceiveFromAny(T)`. O método `ReceiveFromAny(T)` aceita uma matriz de objetos <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> e vincula cada um desses objetos a um objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. Quando você usa o método <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> para vincular um bloco de fluxo de dados de origem a um bloco de destino, a origem propaga as mensagens para o destino à medida que os dados ficam disponíveis. Como a classe <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> aceita somente a primeira mensagem que é oferecida, o método `ReceiveFromAny(T)` produz o resultado chamando o método <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A>. Isso produz a primeira mensagem oferecida ao objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601>. O método <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> tem uma versão sobrecarregada que recebe um objeto <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> com uma propriedade <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.MaxMessages> que, quando é definido como `1`, instrui o bloco de origem a desvincular-se do destino após o destino receber uma mensagem da origem. É importante para o objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> desvincular-se de suas fontes, pois a relação entre a matriz de origens e o objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> não é mais necessária após o objeto <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> receber uma mensagem.  
  
 Para permitir que as chamadas restantes para `TrySolution` terminem após uma delas computar um valor, o método `TrySolution` usa um objeto <xref:System.Threading.CancellationToken>, que é cancelado após o retorno da chamada a `ReceiveFromAny(T)`. O método <xref:System.Threading.SpinWait.SpinUntil%2A> retorna quando esse objeto <xref:System.Threading.CancellationToken> é cancelado.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Copie o código de exemplo e cole-o em um projeto do Visual Studio, ou cole-o em um arquivo chamado `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` para Visual Basic) e, em seguida, execute o seguinte comando em uma janela do prompt de comando do Visual Studio.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**  
  
 Visual Basic  
  
 **vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**  

## <a name="see-also"></a>Consulte também

- [Fluxo de dados](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
