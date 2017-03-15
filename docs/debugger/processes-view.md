---
title: "Exibi&#231;&#227;o de processos | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.externaltools.spyplus.processesview"
helpviewer_keywords: 
  - "tela de Processos"
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exibi&#231;&#227;o de processos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O modo de exibição processos exibe uma árvore de todos os processos ativos no sistema.  O nome do módulo e o ID do processo são mostrados.  Se você quiser examinar um processo do sistema em particular, que geralmente corresponde a um programa em execução, use o modo de exibição de processos.  Processos são identificados por nomes de módulo ou são designados "processos de sistema".  
  
 Microsoft Windows oferece suporte a vários processos.  Cada processo pode ter um ou mais threads e cada segmento pode ter um ou mais associados janelas de nível superior.  Cada janela de nível superior pode possuir uma série de windows.  A \+ símbolo indica que um nível é recolhido.  Modo de exibição recolhido consiste em uma linha por processo.  Clique no símbolo para expandir o nível \+.  
  
 Se você quiser examinar um processo do sistema em particular, que geralmente corresponde a um programa em execução, use o modo de exibição de processos.  Processos são identificados por nomes de módulo ou são designados "processos de sistema". Para localizar um processo, recolher a árvore e procure na lista.  
  
## Procedimentos  
  
#### Para abrir a visualização de processos  
  
1.  Do  **Spy** menu, escolha  **processos**.  
  
 ![Visualização de processos Spy &#43; &#43;](../debugger/media/spy--_processes.png "Spy\+\+\_Processes")  
Visualização de processos Spy \+ \+  
  
 A figura acima mostra a visualização de processos conosco de processo e thread expandidos.  
  
### Nesta seção  
 [Procurando por um processo no modo de exibição de processos](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Explica como localizar um processo específico na visualização de processos.  
  
 [Exibindo propriedades do processo](../debugger/how-to-display-process-properties.md)  
 Explica como exibir mais informações sobre uma mensagem.  
  
### Seções relacionadas  
 [Modos de exibição Spy \+ \+](../debugger/spy-increment-views.md)  
 Explica as exibições de árvore Spy \+ \+ do windows, mensagens, processos e threads.  
  
 [Usando o Spy \+ \+](../debugger/using-spy-increment.md)  
 Apresenta a ferramenta Spy \+ \+ e explica como ele pode ser usado.  
  
 [Caixa de diálogo de pesquisa do processo](../debugger/process-search-dialog-box.md)  
 Usado para localizar o nó para um determinado processo no modo de exibição de processos.  
  
 [Caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md)  
 Exibe as propriedades de um processo selecionado na visualização de processos.  
  
 [Referência Spy \+ \+](../debugger/spy-increment-reference.md)  
 Inclui seções descrevendo cada Spy \+ \+ menu e a caixa de diálogo caixa.