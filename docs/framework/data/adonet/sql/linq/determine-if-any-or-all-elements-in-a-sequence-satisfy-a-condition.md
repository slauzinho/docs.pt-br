---
title: "Determinar se alguns ou todos os elementos em uma sequência satisfazem uma condição"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0dda546c0d8cd073a5d11bdf22805310e3f4f40a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Determinar se alguns ou todos os elementos em uma sequência satisfazem uma condição
O operador de <xref:System.Linq.Enumerable.All%2A> retorna `true` se todos os elementos em uma sequência satisfazem uma condição.  
  
 O operador de <xref:System.Linq.Queryable.Any%2A> retorna `true` se qualquer elemento em uma sequência satisfazem uma condição.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir retorna uma sequência de clientes que possuem pelo menos um pedido. O `Where` / `where` cláusula é avaliada como `true` se o determinado `Customer` tem algum `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Exemplo  
 O seguinte código de Visual Basic determina a lista de clientes que não colocaram pedidos, e assegura que para cada cliente na lista, um nome de contato é fornecido.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Exemplo  
 O exemplo de C# retorna uma sequência de clientes cujos pedidos têm `ShipCity` que começa com “C 2.0”. Também são incluídos no retorno clientes que não têm nenhum pedido. (Por design, o operador de <xref:System.Linq.Queryable.All%2A> retorna `true` para uma sequência vazia.) Os clientes sem pedidos são cortadas na saída de console usando o operador de `Count` .  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de consulta](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)