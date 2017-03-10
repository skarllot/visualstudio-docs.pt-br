---
title: "Depurador de sombreador HLSL | Microsoft Docs"
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
  - "vs.graphics.shaderviewer"
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurador de sombreador HLSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O depurador HLSL no analisador de elementos gráficos do Visual Studio o ajuda a entender como o código do sombreador HLSL opera em condições reais do seu aplicativo.  
  
 Este é o depurador HLSL:  
  
 ![Depuração usando HLSL Assista e janelas de pilha de chamada.](../debugger/media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx\_diag\_demo\_hlsl\_debugger\_orientation")  
  
## Noções básicas do depurador HLSL  
 O depurador HLSL pode ajudar você a entender os problemas que ocorrem no código do sombreador.  A depuração do código HLSL no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se parece com a depuração de código que foi escrito em outras linguagem, como no C\+\+, C\# ou Visual Basic.  Você pode inspecionar o conteúdo das variáveis, definir pontos de interrupção, avançar no código e percorrer até a pilha de chamadas, exatamente como faz ao depurar outras linguagens.  
  
 No entanto, como as GPUs atingem alto desempenho executando código de sombreador em centenas de threads simultaneamente, o depurador HLSL destina\-se para trabalhar com as outras ferramentas do analisador de gráficos para apresentar todas essas informações de uma maneira que faça sentido.  Analisador de gráficos recria quadros capturados usando informações que foram gravadas no log de gráficos; o depurador HLSL não monitora a execução da GPU em tempo real como executar código de sombreador.  Como o log de gráficos contém informações suficientes para recriar qualquer parte da saída e como análise de gráficos fornece ferramentas que podem ajudá\-lo a identificar o pixel exato e o evento onde ocorre um erro, o depurador HLSL precisa apenas simular o thread de sombreador exato que você está interessado.  Isso significa que o trabalho do sombreador pode ser simulado na CPU, onde seu funcionamento interno é no modo de exibição completa.  Isso é o que proporciona ao depurador HLSL uma experiência de depuração parecida com a de uma CPU.  
  
 No entanto, o depurador HLSL, atualmente, encontra\-se limitado por estes motivos:  
  
-   O depurador HLSL não oferece suporte a editar e continuar, mas você pode fazer alterações em seus sombreadores e, em seguida, gere novamente o quadro para ver os resultados.  
  
-   Não é possível depurar um aplicativo e seu código de sombreador ao mesmo tempo.  No entanto, você pode alternar entre eles.  
  
-   É possível adicionar variáveis e registros à janela Inspeção, mas expressões não têm suporte.  
  
 Entretanto, o depurador HLSL oferece a melhor experiência de depuração e mais parecida com a de uma CPU, que de outra forma não seria possível.  
  
## Editar e aplicar sombreador HLSL  
 O depurador de sombreador HLSL não oferece suporte para Editar e Continuar da mesma maneira que o depurador de CPU, porque o modelo de execução GPU não permite que o estado do sombreador seja desfeito.  Em vez disso, o depurador HLSL pode Editar e Aplicar, o que permite que você edite os arquivos de origem HLSL e escolha **Aplicar** para gerar novamente o quadro para ver o efeito das alterações.  O código de sombreador modificado é armazenado em um arquivo separado para preservar a integridade dos arquivos de origem HLSL originais do projeto, mas quando você estiver satisfeito com as alterações você pode escolher **Copiar para...** para copiar as alterações para o seu projeto.  Usando esse recurso, você pode iterar rapidamente no código do sombreador que contém erros e eliminar as etapas caras de recompilação e captura do seu do fluxo de trabalho de depuração do HLSL.  
  
## Desmontagem do HLSL  
 O depurador de sombreador HLSL fornece uma lista de assembly de sombreador HLSL à direita da lista de código\-fonte do HLSL.  
  
## Depurando código HLSL  
 Você pode acessar o depurador HLSL do windows estágios de Pipeline ou histórico de Pixel.  
  
#### Para iniciar o depurador HLSL da janela Estágios de Pipeline Gráficos  
  
1.  Na janela **Gráficos – Estágios de Pipeline**, localize o estágio de pipeline que está associado ao sombreador que deseja depurar.  
  
2.  Abaixo do título do estágio de pipeline, escolha **Iniciar Depuração**, que aparece como uma pequena seta verde.  
  
    > [!NOTE]
    >  Esse ponto de entrada no depurador HLSL depura apenas o primeiro thread do sombreador para o estágio correspondente, isto é, o primeiro vértice ou pixel que é processado.  Você pode usar o histórico de Pixel para acessar outros threads dos estágios desse sombreador.  
  
#### Para iniciar o depurador HLSL do Histórico de Pixel de Gráficos  
  
1.  No **histórico de Pixel de gráficos** janela, expanda a chamada de desenho associada ao sombreador que você deseja depurar.  Cada chamada de desenho pode corresponder a vários primitivos.  
  
2.  Nos detalhes da chamada de desenho, expanda um primitivo cuja contribuição de cor resultante sugira um bug em seu código de sombreador.  Se vários primitivos sugerirem um bug, escolha o primeiro primitivo que o sugere, de modo que você possa evitar uma acumulação de erros, o que pode dificultar o diagnóstico do problema.  
  
3.  Nos detalhes do primitivo, escolha se quer depurar o **Sombreador de Vértices** ou o **Sombreador de Pixel**.  Depure o sombreador de vértices quando você suspeitar que o sombreador de pixel está correto, mas está gerando uma contribuição de cor incorreta porque o sombreador de vértices está passando constantes incorretas a ele.  Caso contrário, depure o sombreador de pixel.  
  
     À direita do sombreador escolhido, escolha **Iniciar Depuração**, que aparece como uma pequena seta verde.  
  
    > [!NOTE]
    >  Esse ponto de entrada no depurador HLSL depura o thread do sombreador de pixel, que corresponde à chamada de desenho, ao primitivo e ao pixel que você escolheu, ou os threads do sombreador de vértices, cujos resultados são interpolados pela chamada de desenho, pelo primitivo e pelo pixel que você escolheu.  No caso de sombreadores de vértices, você ainda pode refinar o ponto de entrada para um vértice específico expandindo os detalhes do sombreador de vértices.  
  
 Para obter exemplos sobre como usar o depurador HLSL para depurar erros de sombreador, consulte [Exemplos de diagnóstico do gráfico](../debugger/graphics-diagnostics-examples.md) ou explicações passo a passo vinculadas na seção Consulte também.  
  
## Consulte também  
 [Instruções passo a passo: objetos ausentes devido ao sombreamento de vértice](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Instruções passo a passo: depurando erros de renderização devido ao sombreamento](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [Instruções passo a passo: usando diagnóstico de gráfico para depurar um sombreador computado](../debugger/walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)