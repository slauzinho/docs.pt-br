---
title: Criando colunas de incremento automático
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cf09732a-ab54-4d98-89e2-4d0a1f28fbce
ms.openlocfilehash: 9c6b5393e1928828bca001ba1d2336f09e64c22c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776931"
---
# <a name="creating-autoincrement-columns"></a>Criando colunas de incremento automático
Para garantir que os valores de coluna exclusiva, você pode definir os valores de coluna para incrementar automaticamente quando novas linhas são adicionadas à tabela. Para criar um incremento automático <xref:System.Data.DataColumn>, defina a <xref:System.Data.DataColumn.AutoIncrement%2A> propriedade da coluna a ser **verdadeiro**. O <xref:System.Data.DataColumn> , em seguida, começa com o valor definido na <xref:System.Data.DataColumn.AutoIncrementSeed%2A> propriedade e, em cada linha adicionada o valor da **AutoIncrement** aumenta o valor definido na coluna a <xref:System.Data.DataColumn.AutoIncrementStep%2A> propriedade da coluna.  
  
 Para **AutoIncrement** colunas, é recomendável que o <xref:System.Data.DataColumn.ReadOnly%2A> propriedade do **DataColumn** ser definido como **true**.  
  
 O exemplo a seguir demonstra como criar uma coluna que começa com um valor de 200 e adiciona de forma incremental nas etapas de 3.  
  
```vb  
Dim workColumn As DataColumn = workTable.Columns.Add( _  
    "CustomerID", typeof(Int32))  
workColumn.AutoIncrement = true  
workColumn.AutoIncrementSeed = 200  
workColumn.AutoIncrementStep = 3  
```  
  
```csharp  
DataColumn workColumn = workTable.Columns.Add(  
    "CustomerID", typeof(Int32));  
workColumn.AutoIncrement = true;  
workColumn.AutoIncrementSeed = 200;  
workColumn.AutoIncrementStep = 3;  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Data.DataColumn>  
 [Definição de esquema de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
