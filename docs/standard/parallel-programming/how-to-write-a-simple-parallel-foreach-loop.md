---
title: Escrever um programa paralelo simples usando Parallel.ForEach
ms.date: 09/12/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cdf4aeb6de027e26687d41d6311b6d7da49e7948
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562210"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Como escrever um loop arallel.ForEach simples

Este exemplo mostra como usar um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> para permitir o paralelismo de dados em relação a qualquer fonte de dados <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.

> [!NOTE]
> Esta documentação usa expressões lambda para definir representantes na PLINQ. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Exemplo

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Um loop <xref:System.Threading.Tasks.Parallel.ForEach%2A> funciona como um loop <xref:System.Threading.Tasks.Parallel.For%2A>. A coleção de origem está particionada e o trabalho é agendado em vários threads com base no ambiente do sistema. Quanto mais processadores houver no sistema, mais rápido o método paralelo será executado. Para alguns conjuntos de origem, um loop sequencial pode ser mais rápido, dependendo do tamanho da origem e do tipo de trabalho que está sendo executado. Para saber mais sobre o desempenho, consulte [Possíveis armadilhas paralelismo de dados e de tarefa](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)

Para saber mais sobre loops paralelos, confira [Como gravar um Loop Parallel.For simples](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Para usar <xref:System.Threading.Tasks.Parallel.ForEach%2A> com uma coleção não genérica, você pode usar o método de extensão <xref:System.Linq.Enumerable.Cast%2A> para converter a coleção em uma coleção genérica, conforme mostra o exemplo a seguir:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Você também pode usar o LINQ Paralelo (PLINQ) para efetuar a paralelização de processamento de fontes de dados <xref:System.Collections.Generic.IEnumerable%601>. O PLINQ permite que você use a sintaxe de consulta declarativa para expressar o comportamento do loop. Para obter mais informações, consulte [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Compilar e executar o código

- Copie e cole este código em um projeto de **Aplicativo de console** do Visual Studio.

- Adicione uma referência a System.Drawing.dll

- Pressione **F5**

## <a name="see-also"></a>Consulte também

- [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programação paralela](../../../docs/standard/parallel-programming/index.md)
- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
