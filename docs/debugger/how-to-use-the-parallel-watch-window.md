---
title: "Como usar a janela Inspe&#231;&#227;o Paralela | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parallelwatch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, janela de inspeção paralela"
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar a janela Inspe&#231;&#227;o Paralela
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Na janela Inspeção Paralela, você pode exibir simultaneamente os valores que uma expressão mantém em vários threads.  Cada linha representa um thread que está sendo executado em um aplicativo, mas um thread pode ser representado em várias linhas.  Mais especificamente, cada linha representa uma chamada de função cuja assinatura de função corresponde à função no registro de ativação atual.  Você pode classificar, reorganizar, remover e agrupar os itens que estão nas colunas.  Você pode sinalizar, remover sinalização, congelar \(suspender\) e descongelar \(retomar\) threads.  As colunas a seguir são exibidas na janela **Inspeção Paralela**:  
  
-   A coluna do sinalizador, na qual você pode marcar um thread ao qual deseja prestar atenção especial.  
  
-   A coluna do quadro, na qual uma seta indica o quadro selecionado.  
  
-   Uma coluna configurável que pode exibir o computador, o processo, o bloco, a tarefa e o thread.  
  
    > [!TIP]
    >  Você deve abrir a janela **Tarefa Paralela** para exibir as informações sobre a tarefa na janela **Inspeção Paralela**.  
  
-   A coluna **\<Adicionar Inspeção\>**, na qual você pode inserir expressões para serem inspecionadas.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para exibir a janela Inspeção Paralela  
  
1.  Defina um ponto de interrupção no código.  
  
2.  Na barra de menus, escolha **Depurar**, **Iniciar Depuração**.  Aguarde até que o aplicativo atinja o ponto de interrupção.  
  
3.  Na barra de menus, escolha **Depurar**, **Janelas**, **Inspeção Paralela** e selecione uma janela de inspeção.  Você pode abrir até quatro janelas.  
  
### Para adicionar uma expressão de inspeção  
  
-   Selecione **\<Adicionar Inspeção\>** e especifique uma expressão de inspeção.  
  
### Para sinalizar ou remover sinalização de um thread  
  
-   Selecione a coluna do sinalizador da linha ou abra o menu de atalho do thread e escolha **Sinalizar** ou **Remover Sinalização**.  
  
### Para exibir somente threads sinalizados  
  
-   Escolha o botão Mostrar Apenas Sinalizados no canto superior esquerdo da janela **Inspeção Paralela**.  
  
### Para alternar quadros  
  
-   Clique duas vezes na coluna do quadro. \(Teclado: selecione a linha e pressione Enter.\)  
  
### Para classificar uma coluna  
  
-   Selecione o título da coluna.  
  
### Para agrupar threads  
  
-   Abra o menu de atalho da janela Inspeção Paralela, escolha **Agrupar por** e selecione o item de submenu apropriado.  
  
### Para congelar ou descongelar threads  
  
-   Abra o menu de atalho da linha e escolha **Congelar** ou **Descongelar**.  
  
### Para exportar os dados na janela Inspeção Paralela  
  
-   Escolha o botão **Abrir no Excel** e, depois, **Abrir no Excel** ou **Exportar para CSV**.  
  
### Para filtrar por uma expressão booliana  
  
-   Insira uma expressão booliana na caixa **Filtrar por Expressão Booliana**.  O depurador avalia a expressão para cada contexto de thread.  Apenas as linhas nas quais o valor é `true` é exibido.  
  
## Consulte também  
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Como usar a janela Threads de GPU](../Topic/How%20to:%20Use%20the%20GPU%20Threads%20Window.md)   
 [Instruções passo a passo: depurando um aplicativo C\+\+ AMP](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)