---
title: '&lt;activityScheduledQuery&gt; do WCF'
ms.date: 03/30/2017
ms.assetid: 25f6eee1-3d98-4c39-b517-c0813f03f106
ms.openlocfilehash: a3c4c8b338921c9d949edd83deb4d6073eb26b55
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123365"
---
# <a name="ltactivityscheduledquerygt-of-wcf"></a>&lt;activityScheduledQuery&gt; do WCF

Representa uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai. A consulta é necessária para um participante de rastreamento assinar os registros de atividade agendada.  
  
Para obter mais informações sobre consultas de perfil de controle, consulte [perfis de acompanhamento](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel>  
\<Acompanhamento >  
\<perfis de >  
\<trackingProfile>  
\<workflow>  
\<activityScheduledQueries >  
\<activityScheduledQuery >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"   
                                  childActivityName="String"/>
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking> 
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`activityName`|Uma cadeia de caracteres que especifica o nome da atividade que está solicitando o cancelamento.|  
|`childActivityName`|Uma cadeia de caracteres que especifica o nome da atividade filho para o qual o cancelamento foi solicitado.|  
  
### <a name="child-elements"></a>Elementos filho

nenhuma.
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<activityScheduledQueries>](activityscheduledqueries-of-wcf.md)|Uma coleção de consultas que são usados para controlar uma atividade agendada para execução por uma atividade pai.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElement>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Acompanhando perfis](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
