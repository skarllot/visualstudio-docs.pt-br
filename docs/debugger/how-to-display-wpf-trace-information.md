---
title: "Como exibir informa&#231;&#245;es de acompanhamento WPF | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
helpviewer_keywords: 
  - "depuração, WPF"
  - "WPF, depuração"
ms.assetid: be3c6859-06e1-459e-9fd0-46375b5f55ef
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como exibir informa&#231;&#245;es de acompanhamento WPF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] pode receber informações de rastreamento de depuração de aplicativos do WPF e exibir essas informações na janela **Saída**.  Para exibir informações de rastreamento de depuração, o rastreamento do WPF deve estar habilitado.  
  
 Você pode habilitar o rastreamento do WPF no arquivo App.config ou programaticamente usando a classe <xref:System.Diagnostics.PresentationTraceSources>.  Uma forma mais fácil de habilitar o rastreamento do WPF é usando a janela **Opções**.  O rastreamento do WPF para aplicativos Web não tem suporte.  
  
### Para habilitar ou personalizar as informações de rastreamento do WPF  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  Na caixa de diálogo **Opções**, na caixa à esquerda, abra o nó **Depuração**.  
  
3.  Em **Depuração**, clique em **Janela de Saída**.  
  
4.  Em **Configurações Gerais de Saída**, selecione **Todas as saídas da depuração**.  
  
5.  Na caixa à direita, procure **Configurações de Rastreamento de WPF**.  
  
6.  Abra o nó **Configurações de Rastreamento de WPF**.  
  
7.  Em **Configurações de Rastreamento de WPF**, clique na categoria de configurações que você deseja habilitar \(por exemplo, **Associação de Dados**\).  
  
     Um controle na lista suspensa aparece na coluna Configurações ao lado de **Associação de Dados** ou de qualquer categoria que você tiver clicado.  
  
8.  Clique na lista suspensa e selecione o tipo de informações de rastreamento que você quer consultar: **Tudo**, **Crítico**, **Erro**, **Aviso**, **Informações**, **Detalhado** ou **ActivityTracing**.  
  
     **Crítico** habilita o rastreamento de eventos Críticos apenas.  
  
     **Erro** habilita o rastreamento de eventos Críticos e de Erro.  
  
     **Aviso** habilita o rastreamento de eventos Críticos, de Erro e Aviso.  
  
     **Informações** habilita o rastreamento de eventos Críticos, de Erro, de Aviso e de Informações.  
  
     **Detalhado** habilita o rastreamento de eventos Críticos, de Erro, de Aviso, de Informações e Detalhado.  
  
     **ActivityTracing** habilita o rastreamento de Parada, Iniciar, Suspender, Transferir e Retomar.  
  
     Para obter mais informações sobre o significado desses níveis de informações de rastreamento, consulte <xref:System.Diagnostics.SourceLevels>.  
  
9. Clique em **OK**.  
  
### Para desabilitar as informações de rastreamento do WPF  
  
1.  No menu **Ferramentas**, selecione **Opções**.  
  
2.  Na caixa de diálogo **Opções**, na caixa à esquerda, abra o nó **Depuração**.  
  
3.  Em **Depuração**, clique em **Janela de Saída**.  
  
4.  Na caixa à direita, procure **Configurações de Rastreamento de WPF**.  
  
5.  Abra o nó **Configurações de Rastreamento de WPF**.  
  
6.  Em **Configurações de Rastreamento de WPF**, clique na categoria de configurações que você deseja habilitar \(por exemplo, **Associação de Dados**\).  
  
     Um controle na lista suspensa aparece na coluna Configurações ao lado de **Associação de Dados** ou de qualquer categoria que você tiver clicado.  
  
7.  Clique na lista suspensa e selecione **Desativar**.  
  
8.  Clique em **OK**.  
  
## Consulte também  
 [Depurando WPF](../debugger/debugging-wpf.md)