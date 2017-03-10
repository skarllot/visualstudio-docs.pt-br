---
title: "Diagn&#243;stico de gr&#225;ficos do Visual Studio | Microsoft Docs"
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
  - "vs.graphics"
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 39
caps.handback.revision: 39
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Diagn&#243;stico de gr&#225;ficos do Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Visual Studio *Diagnóstico de gráficos* é um conjunto de ferramentas de registro e, em seguida, analisando problemas de renderização e desempenho em aplicativos Direct3D.  Diagnóstico de gráficos pode ser usado em aplicativos que estão sendo executados localmente em seu PC com Windows, em um emulador de dispositivo do Windows ou em um dispositivo ou PC remoto.  
  
 O fluxo de trabalho do diagnóstico de gráficos começa com a captura de um registro como o seu aplicativo usa o Direct3D — dinâmicos, à medida que ele é executado, para que seu comportamento pode ser analisado imediatamente, compartilhados ou salvos para posterior.  Sessões de captura podem ser iniciadas e controlado manualmente do Visual Studio ou com a ferramenta de linha de comando capture **dxcap.exe**.  Sessões de captura também podem ser iniciadas e controlado por meio de programação usando os APIs de captura de diagnóstico de gráficos.  
  
 Depois que uma sessão de captura registrou seu conteúdo possa ser reproduzido pelo Visual Studio *gráficos analisador* a qualquer momento, recriando os quadros capturados usando os mesmos recursos exatos e comandos de processamento do aplicativo usado.  Em seguida, usando as ferramentas fornecidas na janela de gráficos Analyer, qualquer um dos quadros capturados podem ser analisados em detalhes.  Essas ferramentas podem ser usadas para examinar qualquer chamada de API do Direct3D, recursos, objeto de estado do pipeline, estágio de pipeline ou até mesmo o histórico completo de qualquer pixel em um quadro capturado.  Usando essas ferramentas em conjunto, um problema de renderização pode ser explorado intuitivamente, desde como ela aparece em um quadro capturado e aprofundar\-se a causa em ativos de código, sombreadores ou gráficos de código\-fonte do aplicativo.  
  
 Para diagnosticar problemas de desempenho, um quadro capturado pode ser analisado usando o *análise de quadro* ferramenta.  Essa ferramenta explora as otimizações de desempenho potencial automaticamente alterando a maneira como o aplicativo usa o Direct3D e benchmark todas as variações para você.  No passado, você pode ter feito e por benchmark esses tipos de alterações manualmente apenas para descobrir quais fez uma diferença de saída.  Com a análise de quadro, basta fazer as alterações que você já souber será compensado.  
  
 Diagnóstico de gráficos ajuda seu aplicativo do Direct3D graficamente ricos examinar e executar o melhor desempenho.  
  
 Continuar [Visão Geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md) para saber mais sobre o que oferece diagnóstico de gráficos do Visual Studio.  
  
## Nesta seção  
 [Visão Geral](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Apresenta o fluxo de trabalho e as ferramentas de Diagnóstico de Gráficos.  
  
 [Guia de Introdução](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 Nesta seção, você aprenderá como instalar o diagnóstico de gráficos do Visual Studio e como começar a usar o diagnóstico de gráficos com seu aplicativo Direct3D.  
  
 [Capturando informações de gráficos](../debugger/capturing-graphics-information.md)  
 Para usar o Diagnóstico de Gráficos para examinar um problema de renderização no aplicativo, primeiro registre informações sobre como o aplicativo usa o DirectX.  Durante a sessão de gravação, enquanto o aplicativo executa normalmente, você *captura* \(ou seja, seleciona\) os quadros de interesse.  A captura contém informações detalhadas sobre como os quadros são renderizados.  É possível salvar as informações capturadas como um documento de log de gráficos para examinar mais tarde ou compartilhar com outros membros da equipe.  
  
 [Uso de GPU](../debugger/gpu-usage.md)  
 Para usar o diagnóstico de gráficos para criar o perfil de seu aplicativo, use a ferramenta de uso de GPU.  Uso GPU pode ser usado em conjunto com outras ferramentas de criação de perfil, como o uso da CPU, para correlacionar a atividade da CPU e GPU que pode causar problemas de desempenho em seu aplicativo.  
  
 [Documentos de log de gráfico](../debugger/graphics-log-document.md)  
 Para começar o exame de um log de gráficos registrado, use a janela de documento de Log de Gráficos para selecionar um quadro capturado \(ou mesmo um pixel específico\) para que seja possível examinar em detalhes os *eventos* \(ou seja, as chamadas à API DirectX\) que o afetam.  
  
 [Análise de Quadros](../debugger/graphics-frame-analysis.md)  
 Depois de selecionar um quadro, use a Análise de Quadros de Gráficos para examinar e ajustar seu desempenho de renderização.  
  
 [Lista de Eventos](../debugger/graphics-event-list.md)  
 Depois de selecionar um quadro, use a **Lista de Eventos de Gráficos** para examinar os eventos e determinar se eles estão relacionados ao problema de renderização.  
  
 [Estado](../debugger/graphics-state.md)  
 A janela de estado ajuda a entender o estado dos gráficos que está ativo no momento do evento atual.  
  
 [Estágios de Pipeline](../debugger/graphics-pipeline-stages.md)  
 Na janela **Estágios de Pipeline Gráficos**, investigue como o evento selecionado no momento é processado pelos estágios do pipeline gráfico para ser possível identificar onde o problema de renderização aparece pela primeira vez.  Examinar os estágios do pipeline é especialmente útil quando um objeto não aparece devido a uma transformação incorreta ou quando um dos estágios produz uma saída que não corresponde ao que o próximo estágio espera.  
  
 [Pilha de Chamadas do Evento](../debugger/graphics-event-call-stack.md)  
 Use a **Pilha de Chamadas do Evento de Gráficos** para examinar a pilha de chamadas do evento selecionado no momento para poder navegar até o código de aplicativo relacionado ao problema de renderização.  
  
 [Histórico de Pixel](../debugger/graphics-pixel-history.md)  
 Usando a janela **Histórico de Pixel de Gráficos** para analisar como o pixel selecionado no momento é afetado pelos eventos que o influenciaram, é possível identificar o evento ou a combinação de eventos que causam certos tipos de problemas de renderização.  O histórico de pixel é especialmente útil quando um objeto é renderizado incorretamente porque a saída do sombreador de pixel está incorreta ou foi combinada incorretamente com o buffer de quadro, ou quando um objeto não aparece porque seus pixels foram descartados antes de atingir o buffer de quadro.  
  
 [Tabela de Objeto](../debugger/graphics-object-table.md)  
 Você usa a **Tabela de Objetos Gráficos** para examinar as propriedades e os conteúdos de objetos e recursos Direct3D específicos em vigor para o evento selecionado no momento.  A tabela de objetos pode ajudar a determinar o contexto do dispositivo gráfico que está ativo durante um evento e examinar os conteúdos de recursos gráficos, como buffers constantes, buffers de vértices e texturas.  
  
 [Depurador HLSL](../debugger/hlsl-shader-debugger.md)  
 Para examinar como o código do sombreador para o evento selecionado no momento e o estágio de pipeline de gráficos se comportam, use **Depurador HLSL** para passar pelo código, examinar os conteúdos das variáveis e realizar outras tarefas típicas de depuração.  Também é possível usar o depurador HLSL para examinar o código do sombreador de computação, independente de os resultados serem processados mais pelo pipeline de gráficos ou apenas relidos pelo aplicativo.  
  
 [Ferramenta de captura de linha de comando](../debugger/command-line-capture-tool.md)  
 Use a ferramenta de captura de linha de comando para capturar e reproduzir rapidamente informações de gráficos sem usar o Visual Studio ou captura programática.  Em particular, você pode usar a ferramenta de captura de linha de comando para automação ou em um ambiente de teste.  
  
 [Exemplos de diagnóstico do gráfico](../debugger/graphics-diagnostics-examples.md)  
 Vários exemplos demonstram como usar as ferramentas de Diagnóstico de Gráficos juntas para diagnosticar diferentes tipos de problemas de renderização.  
  
## Seções relacionadas  
  
|Título|Descrição|  
|------------|---------------|  
|[Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)|Apresenta a funcionalidade de depuração no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Gráficos e jogos DirectX](http://go.microsoft.com/fwlink/?LinkId=256498)|Fornece artigos que discutem as tecnologias de gráficos do DirectX.|