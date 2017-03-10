---
title: "Como subir ou descer a p&#225;gina na mem&#243;ria | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, paginação para cima ou para baixo na memória"
  - "janela de Desmontagem, exibindo espaço de memória"
  - "Janela Memória, paginação para cima ou para baixo na memória"
  - "memória, paginação para cima ou para baixo"
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como subir ou descer a p&#225;gina na mem&#243;ria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando exibe conteúdos de memória na janela de **Memória** ou na janela de **Desmontagem**, você pode usar a barra de rolagem vertical para mover para cima ou para baixo no espaço de memória.  
  
### Para mover para cima ou para baixo na memória  
  
1.  Para rolar a página para baixo \(mover para um endereço de memória superior\), clique na barra de rolagem vertical, abaixo da caixa de rolagem.  
  
2.  Para rolar a página para cima \(mover para um endereço de memória inferior\), clique na barra de rolagem vertical, acima do elevador.  
  
 Você também notará que a barra de rolagem vertical opera de maneira não padrão.  O espaço para endereço de um computador moderno é muito grande e é fácil perder\-se ao segurar o elevador da barra de rolagem e arrastá\-lo a um local aleatório.  Por esse motivo, o elevador é "carregado" e sempre permanece no centro da barra de rolagem.  Em aplicativos de código nativo, você pode rolar a página para cima ou para baixo, mas não pode rolar livremente.  
  
 Em aplicativos gerenciados, a desmontagem é limitada a uma função e você pode rolar normalmente.  
  
 Você observará que os endereços superiores aparecem na parte inferior da janela.  Para exibir um endereço superior, você deve rolar para baixo, não para cima.  
  
#### Para mover para cima ou para baixo em uma instrução  
  
-   Clique na seta na parte superior ou inferior da barra de rolagem vertical.  
  
## Consulte também  
 [Janelas de memória](../debugger/memory-windows.md)   
 [Como usar a janela Desmontagem](../debugger/how-to-use-the-disassembly-window.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)