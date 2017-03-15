---
title: "Como procurar um thread na exibi&#231;&#227;o de threads | Microsoft Docs"
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
  - "threads, procurando"
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como procurar um thread na exibi&#231;&#227;o de threads
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode procurar um segmento específico no modo de exibição de segmentos usando sua seqüência de identificação ou o módulo de thread como critérios de pesquisa.  Você também pode especificar a direção inicial da pesquisa.  Os campos na caixa de diálogo mostrará os atributos da thread selecionada na árvore de thread.  
  
### Para procurar por um segmento no modo de exibição de Threads  
  
1.  Organizar as janelas assim que Spy \+ \+ e um ativo  [Visualização de Threads](../debugger/threads-view.md) janela estão visíveis.  
  
2.  Do  **pesquisa** menu, escolha  **Localizar Thread**.  
  
     O  [Caixa de diálogo de pesquisa de segmento](../debugger/thread-search-dialog-box.md) abre.  
  
3.  Digite a identificação de segmento ou uma seqüência de módulo como critérios de pesquisa.  
  
4.  Desmarque todos os campos para o qual você deseja especificar valores.  
  
    > [!TIP]
    >  Para localizar todos os threads pertencentes a um módulo, desmarque o  **de segmento** nome de caixa de texto e digite o módulo na  **módulo** caixa.  Em seguida, use  **Localizar próxima** para continuar procurando threads.  
  
5.  Escolha  **até** ou  **para baixo** para a direção inicial da pesquisa.  
  
6.  Clique em **OK**.  
  
 Se um thread correspondente for encontrado, ele é realçado na janela de visualização de Threads.