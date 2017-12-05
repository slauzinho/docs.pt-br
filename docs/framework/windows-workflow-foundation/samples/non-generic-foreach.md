---
title: "ForEach não genéricos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8bb78a6f02dd593635c47b8c39a87f40566be1a7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="non-generic-foreach"></a>ForEach não genéricos
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]um conjunto de atividades de fluxo de controle, incluindo é fornecido na sua caixa de ferramentas <xref:System.Activities.Statements.ForEach%601>, que permite a iteração <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` coleções.  
  
 <xref:System.Activities.Statements.ForEach%601>requer seu <xref:System.Activities.Statements.ForEach%601.Values%2A> propriedade para ser do tipo <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable`. Isso impede que usuários de iteração em estruturas de dados que implementam <!--zz <xref:System.Collections.IEnumerable%601> --> `System.Collections.IEnumerable` interface (por exemplo, <xref:System.Collections.ArrayList>). A versão não genérico de <xref:System.Activities.Statements.ForEach%601> supera esse requisito, custas de mais complexidade de tempo de execução para garantir a compatibilidade dos tipos de valores na coleção.  
  
 Este exemplo mostra como implementar uma atividade não genérico de <xref:System.Activities.Statements.ForEach%601> e seu designer. Esta atividade pode ser usada para percorrer <xref:System.Collections.ArrayList>.  
  
## <a name="foreach-activity"></a>Atividade ForEach  
 A declaração de C#/VB `foreach` enumera os elementos de uma coleção, executando uma instrução inserido para cada elemento da coleção. As atividades equivalentes de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] de `foreach` são <xref:System.Activities.Statements.ForEach%601> e <xref:System.Activities.Statements.ParallelForEach%601>. A atividade de <xref:System.Activities.Statements.ForEach%601> contém uma lista de valores e um corpo. Em tempo de execução, a lista é iterada e o corpo é executado para cada valor na lista.  
  
 Para a maioria dos casos, a versão genérica de atividade deve ser a solução preferencial, porque ele aborda a maioria das situações em que ele deve ser usado, e fornece verificação de tipo em tempo de compilação. A versão não genérico pode ser usada iterando por tipos que implementam a interface não genérica de <xref:System.Collections.IEnumerable> .  
  
## <a name="class-definition"></a>Definição de classe  
 O exemplo de código a seguir mostra a definição de uma atividade não genérico de `ForEach` .  
  
```  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }   
}  
```  
  
 Corpo (opcional)  
 <xref:System.Activities.ActivityAction> de tipo <xref:System.Object>, que é executado para cada elemento na coleção. Cada elemento individual é passado no corpo através da propriedade de `Argument` .  
  
 Valores (opcional)  
 A coleção de elementos que são iterados sobre. Garantir que todos os elementos da coleção são de tipos compatíveis é feito em tempo de execução.  
  
## <a name="example-of-using-foreach"></a>Exemplo de usar ForEach  
 O código a seguir demonstra como usar a atividade ForEach em um aplicativo.  
  
```  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>   
       {                          
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|Condição|Mensagem|Severidade|Tipo de exceção|  
|---------------|-------------|--------------|--------------------|  
|Os valores são `null`|O valor para valores de um argumento necessário de atividade “não foi fornecido.|Erro|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a>Designer ForEach  
 O designer de atividade para o exemplo é semelhante a aparência ao designer fornecido para atividades interno de <xref:System.Activities.Statements.ForEach%601> . O designer é exibido na caixa de ferramentas no **exemplos**, **não genérica de atividades** categoria. O designer é denominado **ForEachWithBodyFactory** na caixa de ferramentas, porque a atividade expõe um <xref:System.Activities.Presentation.IActivityTemplateFactory> na caixa de ferramentas, que cria a atividade com configurada adequadamente <xref:System.Activities.ActivityAction>.  
  
```  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a>Para executar este exemplo  
  
1.  Defina o projeto de sua escolha como o projeto inicialização de solução:  
  
    1.  **CodeTestClient** mostra como usar a atividade usando o código.  
  
    2.  **DesignerTestClient** mostra como usar a atividade no designer.  
  
2.  Compile e execute o projeto.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`