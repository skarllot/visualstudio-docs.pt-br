---
title: "Atribui&#231;&#245;es de porta do depurador remoto | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Atribui&#231;&#245;es de porta do depurador remoto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O depurador remoto do Visual Studio pode ser executado como um aplicativo ou como um serviço em segundo plano. Quando ele é executado como um aplicativo, ele usa uma porta atribuída por padrão, da seguinte maneira:  
  
-   O Visual Studio 2015:4020  
  
-   O Visual Studio 2013:4018  
  
-   O Visual Studio 2012:4016  
  
 Em outras palavras, o número da porta atribuída ao depurador remoto é incrementado por 2 para cada versão. Você pode definir um número de porta diferente do que você deseja. Explicaremos como configurar números de porta em uma seção posterior.  
  
## A porta do depurador remoto em sistemas operacionais de 32 bits  
 4020 TCP \(no Visual Studio de 2015\) é a porta principal e é necessário para todos os cenários. Você pode configurar isso de linha de comando ou a janela do depurador remoto.  
  
 Na janela do depurador remoto, clique em **Ferramentas \/ opções**, e definir o número de porta TCP\/IP.  
  
 Na linha de comando, iniciar o depurador remoto com o **\/porta** alternar: **msvsmon \/port \< número da porta \>**.  
  
 Você pode encontrar o depurador remoto opções de linha de comando na Ajuda de depuração remota \(pressione **F1** ou clique **Ajuda \/ uso** na janela do depurador remoto\).  
  
## A porta do depurador remoto em sistemas operacionais de 64 bits  
 Quando a versão de 64 bits do depurador remoto for iniciada, ele usa a porta 4020 por padrão.  Se você depurar um processo de 32 bits, a versão de 64 bits do depurador remoto inicia uma versão de 32 bits do depurador remoto na porta 4021. Se você executar o depurador remoto de 32 bits, ele usa 4020 e 4021 não é usado.  
  
 Esta porta é configurável pela linha de comando: **\/wow64port Msvsmon \< número da porta \>**.  
  
## A porta de descoberta  
 UDP 3702 é usado para localizar instâncias em execução do depurador remoto na rede \(por exemplo, o **localizar** caixa de diálogo no **Attach to Process** caixa de diálogo\). Ele é usado apenas para descobrir um computador executando o depurador remoto, portanto, é opcional se você tiver alguma outra forma de saber o nome do computador ou endereço IP do computador de destino. Essa é uma porta padrão para a descoberta, portanto o número da porta não pode ser configurado.  
  
 Se não desejar habilitar a descoberta, você pode iniciar o msvsmon da linha de comando com a descoberta desabilitada:  **Msvsmon \/nodiscovery**.  
  
## Portas do depurador remoto no Azure  
 As seguintes portas são usadas pelo depurador remoto no Azure. As portas de serviço em nuvem são mapeadas para as portas na máquina virtual individual. Todas as portas são TCP.  
  
||||  
|-|-|-|  
|**Conexão**|**Porta de serviço de nuvem**|**Porta na VM**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## Consulte também  
 [Depuração remota](../debugger/remote-debugging.md)