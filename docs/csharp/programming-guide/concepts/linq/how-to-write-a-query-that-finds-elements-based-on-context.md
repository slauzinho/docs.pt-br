---
title: Como escrever uma consulta que encontra elementos com base no contexto (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: c1c43bc47df1612be26c78351a9d30272a020160
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45987949"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a>Como escrever uma consulta que encontra elementos com base no contexto (C#)
Muitas vezes você pode ter que escrever uma consulta que seleciona elementos com base no contexto. Você pode querer filtrar com base nos elementos irmãos precedentes ou seguintes. Você pode querer filtrar com base nos elementos filhos ou ancestrais.  
  
 Você pode fazer isso escrevendo uma consulta e usando os resultados da consulta na cláusula `where`. Se você primeiro tiver que testar com zero e, em seguida, testar o valor, é mais conveniente fazer a consulta em uma cláusula `let` e usar os resultados na cláusula `where`.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir seleciona todos os elementos `p` que são imediatamente seguidos por um elemento `ul`.  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Esse código gera a seguinte saída:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma consulta para XML que está em um namespace. Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 Esse código gera a seguinte saída:  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement.Parse%2A>  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>  
- [Consultas básicas (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
