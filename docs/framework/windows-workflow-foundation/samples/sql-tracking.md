---
title: Rastreamento de SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c2b9eb78c6d8e7125d65ec8fea4c1611ac55e2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="sql-tracking"></a>Rastreamento de SQL
Este exemplo demonstra como escrever um participante de rastreamento SQL personalizado, que grava registros de rastreamento em uma base de dados SQL. [!INCLUDE[wf](../../../../includes/wf-md.md)] fornece o rastreamento de fluxo de trabalho a visibilidade de ganho em execução de uma instância de fluxo de trabalho. O tempo de execução de rastreamento emite-se registros de acompanhamento de fluxo de trabalho durante a execução de fluxo de trabalho. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]fluxo de trabalho de controle de alterações, consulte [fluxo de trabalho de rastreamento e rastreamento](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Verifique têm SQL Server 2008, SQL Server 2008 Express edition ou mais recente instalados. Os scripts agrupados com o exemplo assumem o uso de uma instância do SQL express em seu computador local. Se você tiver uma instância diferente por favor alterar os scripts base de dados - relacionados antes de executar o exemplo.  
  
2.  Crie o SQL Server que controla o base de dados executando Trackingsetup.cmd no diretório de scripts (\ \ WF básico rastreamento SqlTracking \ \ \ \ CS scripts). Isso cria um base de dados chamado TrackingSample.  
  
    > [!NOTE]
    >  O script cria o base de dados na instância padrão do SQL express. Se você deseja instalá-lo em uma instância diferente de base de dados, editar script de Trackingsetup.cmd.  
  
3.  Abra SqlTrackingSample.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Pressione CTRL+SHIFT+B para criar a solução.  
  
5.  Pressione F5 para executar o aplicativo.  
  
     A janela do navegador abre e mostra a listagem de diretório para o aplicativo.  
  
6.  No navegador, clique StockPriceService.xamlx.  
  
7.  O navegador exibe a página de StockPriceService, que contém o endereço de WSDL de serviço local. Copie este endereço.  
  
     Um exemplo de endereço de WSDL de serviço local é http://localhost:65193/StockPriceService.xamlx?wsdl.  
  
8.  Usando [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], execute o cliente de teste de WCF (WcfTestClient.exe). Está localizado no Microsoft Visual Studio 10.0 diretório \ Common7 \ IDE.  
  
9. No cliente de teste do WCF, clique o **arquivo** menu e selecione **Adicionar serviço**. Cole o endereço do serviço local na caixa de texto. Clique em **Okey** para fechar a caixa de diálogo.  
  
10. O cliente de teste do WCF, clique duas vezes em **GetStockPrice**. Isso abre o `GetStockPrice` operação que usa um parâmetro, digite o valor `Contoso` e clique em **Invoke**.  
  
11. Os registros emissores de rastreamento são gravados em uma base de dados SQL. Para exibir os registros de rastreamento, abra o base de dados de TrackingSample em SQL Management Studio e navegar para tabelas. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SQL Server Management Studio, consulte [apresentando o SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645). SQL Server 2008 Management Studio Express pode ser baixado [aqui](http://go.microsoft.com/fwlink/?LinkId=180520). Executar uma consulta selecionar as tabelas exibe os dados dentro dos registros de rastreamento armazenados nas tabelas respectivas.  
  
#### <a name="to-uninstall-the-sample"></a>Para desinstalar o exemplo  
  
1.  Execute o script de theTrackingcleanup.cmd no diretório de exemplo (\ \ WF básico \ \ rastreamento SqlTracking).  
  
    > [!NOTE]
    >  O Trackingcleanup.cmd tentar excluir o base de dados em seu computador local SQL express. Se você estiver usando outra instância do SQL server, editar Trackingcleanup.cmd.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)