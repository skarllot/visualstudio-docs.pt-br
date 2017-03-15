---
title: "Como alterar a m&#225;quina de reprodu&#231;&#227;o de diagn&#243;stico do gr&#225;fico | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como alterar a m&#225;quina de reprodu&#231;&#227;o de diagn&#243;stico do gr&#225;fico
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode executar novamente as informações de gráficos usando seu computador local ou usando um computador remoto ou um dispositivo.  
  
## Escolhendo um computador de reprodução  
 A máquina de reprodução é um computador ou dispositivo que é usado para executar eventos gráficos de um log gráfico.  Geralmente, o computador local é a opção mais conveniente, mas um problema de renderização não pode reproduzir em um computador que tem versões de hardware ou de driver diferentes do computador onde ele foi capturado; quando isso acontece, você pode escolher um computador de reprodução remoto que melhor reproduza o problema e ainda usar o seu computador de desenvolvimento para diagnosticá\-lo.  
  
#### Para usar o computador local para reproduzir informações gráficas  
  
1.  Na janela do documento Log de Elementos Gráficos, escolha o link **Máquina de Reprodução** .  A caixa de diálogo **Selecionar Conexões do Depurador** aparece.  
  
2.  Em **Configuração Manual**, na propriedade **Endereço**, digite `localhost`.  
  
3.  Defina a propriedade de **Modo de Autenticação** como **Nenhum**.  
  
4.  Escolha o botão **Selecionar**.  
  
#### Para usar um computador remoto para reproduzir informações gráficas  
  
1.  Na janela do documento Log de Elementos Gráficos, escolha o link **Máquina de Reprodução** .  A caixa de diálogo **Selecionar Conexões do Depurador** aparece.  
  
2.  Em **Configuração Manual**, na propriedade **Endereço**, digite o nome de domínio do Windows ou o endereço IP do computador ou dispositivo que você deseja usar para reproduzir as informações gráficas.  
  
3.  Especificar o tipo de autorização que você deseja usar para proteger a conexão para o computador da reprodução.  
  
    -   Para Autenticação Windows, defina a propriedade de **Modo de autenticação** como **Windows**.  
  
    -   Para nenhuma autenticação, defina a propriedade de **Modo de autenticação** como **Nenhum**.  
  
4.  Escolha o botão **Selecionar**.  
  
> [!NOTE]
>  A caixa de diálogo **Selecionar Conexões do Depurador** também pode exibir os destinos de depuração remota conectados diretamente ao seu computador de desenvolvimento ou que estão na mesma subrede.  Você pode usar um desses destinos de depuração remota como o computador de reprodução de diagnósticos gráficos sem configurá\-lo manualmente.  Na caixa de diálogo **Selecionar Conexões do Depurador** selecione o destino desejado e escolha o botão **Selecionar**.  
  
## Consulte também  
 [Documentos de log de gráfico](../debugger/graphics-log-document.md)