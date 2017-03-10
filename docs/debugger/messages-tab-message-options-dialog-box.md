---
title: "Guia Mensagens, Caixa de di&#225;logo Op&#231;&#245;es da Mensagem | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "opções de mensagem, Mensagens"
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Mensagens, Caixa de di&#225;logo Op&#231;&#245;es da Mensagem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o  **mensagens** tab para selecionar qual mensagem tipos de lista em  [o modo de exibição de mensagens](../debugger/messages-view.md)e para especificar os critérios de pesquisa de mensagem.  Para exibir o  [Caixa de diálogo de opções de mensagem](../debugger/message-options-dialog-box.md), escolha  **Mensagens de Log** da  **Spy** menu.  
  
 Em geral, selecione primeiro  **Mensagem grupos**e então ajustar a seleção selecionando individuais  **mensagens ao modo de exibição**.  O  **todos os** botão seleciona todos os tipos de mensagem e o  **Nenhum** botão limpa todos os tipos.  
  
 As configurações a seguir estão disponíveis na  **mensagens** guia:  
  
 **Mensagens para o modo de exibição**  
 Selecione mensagens específicas para exibição.  Quando você cria uma nova janela de mensagens, ele pode exibir todas as mensagens.  Quando você filtra mensagens da  **mensagens** guia, esse filtro só se aplica às novas mensagens, não as mensagens que já foram exibidas no modo de exibição do Windows.  
  
 **Grupos de mensagens**  
 Selecione os grupos de mensagem para exibição.  Os grupos disponíveis incluem:  
  
-   MeuInt: com um código de maior ou igual a MeuInt  
  
-   Registrado: registrado com o  **RegisterWindowMessage** de chamada  
  
-   Desconhecido: mensagens de desconhecidos no intervalo de 0 a \(MeuInt – 1\)  
  
 Observe que esses  **Mensagem grupos** não correspondem às entradas específicas em  **Mensagens para exibição**.  Quando você seleciona um grupo, a seleção é aplicada diretamente ao fluxo de mensagens.  
  
 Uma caixa de seleção cinza no  **Mensagem grupos** indica que o  **Mensagens para exibição** caixa de listagem foi modificada para mensagens naquele grupo; nem todos os tipos de mensagens desse grupo estão selecionados.  
  
 **Salvar configurações como padrão**  
 Salve as configurações atuais para uso posterior como opções de pesquisa da mensagem.  Essas configurações também são salvos ao sair Spy \+ \+.