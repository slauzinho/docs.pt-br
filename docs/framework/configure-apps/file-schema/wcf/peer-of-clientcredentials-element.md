---
title: '&lt;par&gt; do elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 9d63aaaa6404b791559d1288730098075f1fd8eb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504477"
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a>&lt;par&gt; do elemento &lt;clientCredentials&gt;
Especifica as credenciais usadas ao autenticar clientes ponto a ponto.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<comportamento de >  
\<clientCredentials>  
\<par >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|Especifica um certificado X.509 a ser usado para assinar e criptografar mensagens para clientes ponto a ponto. .|  
|[\<peerAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|Especifica as opções de autenticação para clientes ponto a ponto.|  
|[\<messageSenderAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|Especifica opções de autenticação para remetentes de mensagens.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Especifica as credenciais usadas para autenticar um cliente para um serviço.|  
  
## <a name="remarks"></a>Comentários  
 Este elemento de configuração especifica as credenciais que um nó par usa para se autenticar em outros nós na malha, bem como configurações de autenticação que um nó par usa para autenticar outros nós pares. Para obter mais informações, consulte [autenticação de mensagem de canal par](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95) e [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [Rede ponto a ponto](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [Protegendo clientes](../../../../../docs/framework/wcf/securing-clients.md)  
 [Autenticação de mensagem de canal par](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [Autenticação personalizada de canal par](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [Protegendo aplicativos de canal par](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
