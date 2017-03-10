---
title: "Como procurar uma janela na exibi&#231;&#227;o de janelas | Microsoft Docs"
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
  - "janelas, pesquisando na exibição Janelas"
ms.assetid: 30306970-b861-4315-acf8-f86a43d4e73b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como procurar uma janela na exibi&#231;&#227;o de janelas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode procurar por uma janela específica no modo de exibição do Windows usando sua alça, legenda, classe ou uma combinação de sua legenda e uma classe como critérios de pesquisa.  Você também pode especificar a direção inicial da pesquisa.  Os campos na caixa de diálogo mostrará os atributos da janela selecionada na árvore de janela.  
  
 Iniciar com a árvore expandida para o segundo nível \(todas as janelas que são filhos da área de trabalho\), para que você possa identificar o nível de desktop windows por seus nomes de classe e o título.  Depois de ter escolhido uma janela de nível de área de trabalho, você pode expandir esse nível para localizar uma janela filho específicos.  
  
### Para procurar por uma janela no modo de exibição do Windows  
  
1.  Organizar as janelas assim que Spy \+ \+, o  [De exibição do Windows](../debugger/windows-view.md) janela e a janela de destino estão visíveis.  
  
2.  Do  **pesquisa** menu, escolha  **Janela Localizar**.  
  
     O  [Caixa de diálogo de pesquisa de janela](../debugger/window-search-dialog-box.md) abre.  
  
    > [!TIP]
    >  Para reduzir a desordem na tela, selecione o  **Spy ocultar** opção.  Essa opção oculta a janela principal do Spy \+ \+ e deixa apenas o  **Janela pesquisa** caixa de diálogo visível em relação os outros aplicativos.  A janela principal do Spy \+ \+ é restaurada quando você clica em  **OK** ou  **Cancelar**, ou quando você desmarca a  **Ocultar Spy \+ \+** opção.  
  
3.  Arraste o  **Ferramenta de localização de** sobre a janela de destino.  Ao arrastar a ferramenta, o  **Janela pesquisa** caixa de diálogo exibe os detalhes na janela selecionada.  
  
     \- ou \-  
  
     Se você souber o identificador da janela desejado \(por exemplo, do depurador\), digite\-o  **tratar** caixa.  
  
     \- ou \-  
  
     Se você souber a legenda e\/ou a classe da janela você deseja, você pode digitá\-los a  **legenda** e  **classe** caixas de texto e limpar o  **tratar** caixa de texto.  
  
4.  Escolha  **até** ou  **para baixo** para a direção inicial da pesquisa.  
  
5.  Clique em **OK**.  
  
     Se uma janela correspondente for encontrada, ele é realçado no  [De exibição do Windows](../debugger/windows-view.md) janela.