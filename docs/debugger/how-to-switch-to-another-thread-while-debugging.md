---
title: "Como alternar para outro thread durante a depura&#231;&#227;o | Microsoft Docs"
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
helpviewer_keywords: 
  - "threads, trocando [depurando]"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como alternar para outro thread durante a depura&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando você depura um aplicativo de vários threads, pode usar qualquer dos vários métodos para alternar o contexto do thread com o qual você vem trabalhando para outro thread.  
  
### Para alternar para determinado thread exibido na janela de threads  
  
-   Clique duas vezes no thread.  
  
### Para alternar para um thread em uma janela de origem  
  
-   Na medianiz esquerda, clique com o botão direito em um indicador de thread, aponte para **Alternar para**e clique no nome desse thread para o qual você deseja alternar.  O menu de atalho mostra apenas os threads nesse local específico.  
  
     Se nenhum indicador for exibido, clique com o botão direito na janela **Threads** e verifique se **Mostrar Threads em Origem** está selecionado.  
  
### Para alternar para um thread na barra de ferramentas do Local de Depuração  
  
1.  Na barra de ferramentas **Local de Depuração**, clique na caixa **Thread**.  
  
2.  Na lista, clique no thread para o qual você deseja alternar.  
  
## Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)