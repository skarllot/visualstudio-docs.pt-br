---
title: "Como procurar um processo na exibi&#231;&#227;o de processos | Microsoft Docs"
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
  - "tela de Processos"
  - "processos, procurando"
ms.assetid: 7cb97b37-4a95-4f1b-9eee-4910aa9c115b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como procurar um processo na exibi&#231;&#227;o de processos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode procurar um processo específico no modo de exibição de processos por meio de sua seqüência de identificação ou o módulo de processo como critérios de pesquisa.  Você também pode especificar a direção inicial da pesquisa.  Os campos na caixa de diálogo mostrará os atributos do processo selecionado na árvore de processo.  
  
### Para procurar por um processo no modo de exibição de processos  
  
1.  Organizar as janelas assim que Spy \+ \+ e um ativo  [Processos de modo de exibição](../debugger/processes-view.md) janela estão visíveis.  
  
2.  Do  **pesquisa** menu, escolha  **Processo de localizar**  
  
     O  [Caixa de diálogo de pesquisa do processo](../debugger/process-search-dialog-box.md) abre.  
  
3.  Digite a identificação do processo ou uma seqüência de módulo como critérios de pesquisa.  
  
4.  Desmarque todos os campos para o qual você deseja especificar valores.  
  
    > [!TIP]
    >  Para localizar todos os processos pertencentes a um módulo, desmarque o  **processo** caixa e digite o nome do módulo do  **módulo** caixa.  Em seguida, use  **Localizar próxima** para continuar a pesquisa de processos.  
  
5.  Escolha  **até** ou  **para baixo** para a direção inicial da pesquisa.  
  
6.  Clique em **OK**.  
  
 Se um processo de correspondência for encontrado, ele é realçado no  **exibição processo** janela.