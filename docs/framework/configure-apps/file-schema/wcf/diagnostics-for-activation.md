---
title: "&lt;diagnósticos&gt; de ativação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1610c77125d2820e3adc06b3c37177058c85abdd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt-for-activation"></a>&lt;diagnósticos&gt; de ativação
Configura [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] funcionalidades de diagnóstico do ouvinte.  
  
 \<system.serviceModel.activation >  
\<diagnóstico >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`performanceCountersEnabled`|Um valor booliano que indica se os contadores de desempenho estão habilitados para fins de diagnóstico.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Contém definições de configuração para o processo do ouvinte SMSvcHost.exe.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>