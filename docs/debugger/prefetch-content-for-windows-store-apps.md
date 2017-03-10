---
title: "Executar pr&#233;-busca de conte&#250;do para aplicativos da Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Executar pr&#233;-busca de conte&#250;do para aplicativos da Windows Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para deixar seu aplicativo da Windows Store mais ágil na resposta, você pode solicitar ao Windows para pré\-carregar algum conteúdo da Web, como páginas ou imagens da Web, no cache [WinINet](http://msdn.microsoft.com/pt-br/0a06f2af-957a-4dff-a8cc-187370181b5c) [WinINet](http://msdn.microsoft.com/library/aa383630.aspx) do aplicativo. Essa funcionalidade chama\-se pré\-busca. É especialmente eficiente para o conteúdo que é usado na inicialização, mas você também pode executar a pré\-busca de outro conteúdo usado frequentemente. Os métodos da classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) permitem especificar os URIs do conteúdo que você deseja pré\-carregar. Consulte o SDK do Windows [Amostra de pré\-busca de conteúdo](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309) para obter exemplos de como adicionar a funcionalidade ContentPrefetcher ao seu aplicativo.  
  
 O Windows usa heurística para determinar quando e se a pré\-busca deve ocorrer e quais recursos serão baixados. A heurística leva em conta condições de energia e rede do sistema da conta, o histórico de uso do aplicativo do usuário e os resultados das tentativas anteriores de pré\-busca. No Visual Studio, você pode usar o comando **Acionar Pré\-busca de Aplicativo da Windows Store** para forçar o Windows a ignorar a heurística ContentPrefetcher e pré\-carregar todo o conteúdo da Web especificado. Isso pode ser útil se você quiser testar o comportamento ou o desempenho do aplicativo com o conteúdo para pré\-buscar em um estado conhecido \(carregado ou não carregado\).  
  
## Para forçar o pré\-carregamento dos recursos especificados do ContentPrefetcher  
 Este procedimento presume que você já definiu a funcionalidade ContentPrefetcher e especificou os URIs de conteúdo a pré\-carregar em seu projeto de aplicativo. Para forçar o pré\-carregamento de conteúdo quando os recursos especificados são novos ou modificados, você tem de iniciar e parar o aplicativo antes de escolher o comando **Acionar Pré\-busca de Aplicativo da Windows Store**. Você executa o aplicativo primeiro para registrar os URIs. O comando **Acionar Pré\-busca de Aplicativo da Windows Store** força o ContentPrefetcher a baixar o conteúdo e adicioná\-lo ao cache. Nas execuções subsequentes do aplicativo, você pode presumir que o conteúdo esteja pré\-carregado.  
  
1.  Inicie o aplicativo para registrar os URIs de conteúdo para pré\-busca com o aplicativo. No menu **Depurar**, escolha **Iniciar Depuração** \(atalho do teclado: F5\).  
  
2.  No menu **Depurar**, escolha **Parar Depuração** \(atalho do teclado: Shift\+F5\).  
  
3.  No menu **Depurar**, escolha **Outros Destinos de Depuração** e escolha **Acionar Pré\-busca de Aplicativo da Windows Store**.  
  
 Agora você pode depurar, testar ou analisar seu aplicativo com os recursos Web pré\-buscados.  
  
> [!NOTE]
>  Repita estas etapas sempre que adicionarem ou modificar o conteúdo da Web especificado.  
  
## Consulte também  
 [Postagem do blog: Como acionar a pré\-busca de aplicativos da Windows Store no Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)