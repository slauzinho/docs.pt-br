---
title: Negociação de segurança e tempo limite
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
author: BrucePerlerMS
ms.openlocfilehash: 6b6c9c6ed44eb3ebefb21f2fbff1e73171262ed7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194891"
---
# <a name="security-negotiation-and-timeouts"></a>Negociação de segurança e tempo limite
Quando os clientes e serviços de autenticação, o Windows Communication Foundation (WCF) suporta um modo em que a credencial de serviço é negociada como parte da autenticação. Nesses cenários, uma troca potencialmente multi-segmentos ocorre entre o cliente e o serviço para propagar a credencial de serviço ao cliente. O <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> propriedade controla o quanto o exchange multi-segmentos pode demorar para ser concluída. No entanto, esse tempo limite se aplica somente se o exchange, na verdade, demorar mais que uma única solicitação-resposta. Em casos em que a negociação é realizada em uma única ida e volta, o tempo limite não se aplica.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [Como definir uma distorção máxima do relógio](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
