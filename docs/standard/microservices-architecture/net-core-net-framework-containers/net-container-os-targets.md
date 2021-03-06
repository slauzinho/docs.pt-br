---
title: Para qual sistema operacional direcionar com os contêineres do .NET
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Para qual sistema operacional direcionar com os contêineres do .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: b2ae1d2e732f152133dd8a8757b955e05cdd88eb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "45970819"
---
# <a name="what-os-to-target-with-net-containers"></a>Para qual sistema operacional direcionar com os contêineres do .NET

Dada a diversidade de sistemas operacionais compatíveis com o Docker e as diferenças entre o .NET Framework e o .NET Core, você deve direcionar um sistema operacional e versões específicos dependendo da estrutura que você está usando.

Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server. Essas versões do Windows oferecem características diferentes (IIS no Windows Server Core versus um servidor Web auto-hospedado como Kestrel no Nano Server) que podem ser exigidas pelo .NET Framework ou pelo .NET Core, respectivamente.

Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).

Na Figure 3-1, é possível ver a possível versão do sistema operacional dependendo do .NET Framework usado.

![Ao implantar aplicativos .NET Framework herdados, é necessário definir o Windows Server Core como destino, compatível com aplicativos herdados e o IIS e com uma imagem maior. Ao implantar aplicativos .NET Core, é possível definir o Windows Nano Server como destino, que é otimizado para nuvem, usa o Kestrel, é menor e inicia mais rapidamente. Também é possível definir Linux, Debian de suporte, Alpine e outros como destino. Também usa o Kestrel, é menor e inicia mais rapidamente.](./media/image1.png)

**Figura 3-1.** Sistemas operacionais a serem direcionados dependendo das versões do .NET Framework

Também é possível criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição diferente do Linux ou em que você quer uma imagem com versões não fornecidas pela Microsoft. Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework tradicional e no Windows Server Core, que é um cenário não tão comum para Docker.

Ao adicionar o nome de imagem ao seu arquivo Dockerfile, é possível selecionar o sistema operacional e a versão dependendo da marcação usada, como nos seguintes exemplos:

<table>
<thead>
<tr class="header">
<th>Image</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr>
<td>microsoft/dotnet:2.1-runtime</td>
<td>Várias arquiteturas .NET Core 2.1: dá suporte ao Linux e ao Windows Nano Server dependendo do host do Docker.</td>
</tr>
<tr class="odd">
<td>microsoft/dotnet:2.1-aspnetcore-runtime</td>
<td><p>Várias arquiteturas ASP.NET Core 2.1: dá suporte ao Linux e ao Windows Nano Server dependendo do host do Docker.</p>
<p>A imagem aspnetcore tem algumas otimizações para ASP.NET Core.</p></td>
</tr>
<tr class="even">
<td>microsoft/dotnet:2.1-aspnetcore-runtime-alpine</td>
<td>Tempo de execução do .NET Core 2.1 – somente na distribuição do Linux Alpine</td>
</tr>
<tr class="odd">
<td>microsoft/dotnet:2.1-aspnetcore-runtime-nanoserver-1803</td>
<td>Tempo de execução do .NET Core 2.1 – somente no Windows Nano Server (Windows Server versão 1803)</td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
[Anterior](container-framework-choice-factors.md)
[Próximo](official-net-docker-images.md)
