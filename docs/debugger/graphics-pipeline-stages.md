---
title: "Est&#225;gios de Pipeline Gr&#225;ficos | Microsoft Docs"
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
  - "vs.graphics.pipeline"
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Est&#225;gios de Pipeline Gr&#225;ficos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A janela estágios de Pipeline gráficos ajuda a entender como uma chamada de desenho individuais é transformada por cada estágio do pipeline de gráficos do Direct3D.  
  
 Esta é a janela estágios de Pipeline:  
  
 ![Um objeto 3D passa por estágios de pipeline.](../debugger/media/gfx_diag_demo_pipeline_stages_orientation.png "gfx\_diag\_demo\_pipeline\_stages\_orientation")  
  
## Noções básicas sobre a janela Estágios de Pipeline Gráficos  
 A janela estágios de Pipeline visualiza o resultado de cada estágio do pipeline gráfico separadamente para cada chamada de desenho.  Normalmente, os resultados dos estágios no meio do pipeline estiverem ocultos, tornando difícil saber onde iniciou um problema de renderização.  Visualizando separadamente cada estágio, a janela estágios de Pipeline torna mais fácil ver onde o problema começa — por exemplo, você pode ver facilmente quando o estágio de sombreador de vértices inesperadamente faz com que um objeto a ser desenhado fora da tela.  
  
 Depois de identificar o estágio em que o problema ocorrer, você pode usar outras ferramentas do analisador de gráficos para examinar como os dados foram interpretados ou transformados.  Problemas de renderização que aparecem nos estágios de pipeline costumam descritores de formato de vértice relacionados ao incorreto, programas de sombreador com bugs ou estado configurado incorretamente.  
  
### Links para objetos gráficos relacionados  
 Contexto adicional, às vezes, é necessário determinar por que uma chamada de desenho interage de uma maneira específica com o pipeline de gráficos.  Para facilitar a localização deste contexto adicional, os links de janela estágios de Pipeline gráficos para um ou mais objetos que fornecem contexto adicional relacionado ao que está acontecendo no pipeline gráfica.  
  
-   No Direct3D 12 esse objeto é geralmente uma lista de comandos.  
  
-   No Direct3D 11 esse objeto é geralmente um contexto de dispositivo de gráficos.  
  
 Esses links são parte da assinatura de evento gráfico atual está localizada no canto superior esquerdo da janela estágios de Pipeline gráficos.  Siga qualquer um desses links para examinar os detalhes adicionais sobre o objeto.  
  
### Exibição e depuração do código do sombreador  
 Você pode examinar e depurar o código de vértice, hull, domínio, geometry e pixel shaders usando os controles na parte inferior de seus respectivos estágios na janela estágios de Pipeline.  
  
##### Para exibir o código\-fonte do sombreador  
  
-   No **estágios de Pipeline gráficos** janela, localize o estágio de sombreador que corresponde ao sombreador que deseja examinar.  Em seguida, abaixo da imagem de visualização, siga o link de título do estágio de sombreador — por exemplo, siga o link **sombreador de vértices obj:30** para exibir o código de origem do sombreador de vértice.  
  
    > [!TIP]
    >  O número de objeto **obj:30**, identifica esse sombreador em toda a interface de analisador de gráficos como a janela de histórico de tabela e de pixel do objeto.  
  
##### Para depurar um sombreador  
  
-   No **estágios de Pipeline gráficos** janela, localize o estágio de sombreador que corresponde ao sombreador que deseja depurar.  Em seguida, abaixo da imagem de visualização, escolha **Iniciar depuração**.  Esse ponto de entrada para os padrões de depurador HLSL para a primeira invocação do sombreador para o estágio correspondente — ou seja, o primeiro pixel, vértice ou primitivo que é processado pelo sombreador durante a chamada de desenho.  Invocações desse sombreador para um vértice ou pixel específico podem ser acessadas por meio de **histórico de Pixel de gráficos**.  
  
### Os estágios de pipeline  
 A janela estágios de Pipeline visualiza apenas os estágios de pipeline que estavam ativos durante a chamada de desenho.  Cada estágio do pipeline gráfica transforma uma entrada do estágio anterior e passa o resultado para o próximo estágio.  O primeiro estágio, o Assembler entrada — extrai dados de índice e vértice de seu aplicativo como sua entrada; o último estágio — Output Merger — combina recentemente renderizado pixels junto com o conteúdo atual do framebuffer ou destino de renderização como sua saída para gerar a imagem final que você vê na tela.  
  
> [!NOTE]
>  Os sombreadores de cálculo não são compatíveis com a janela **Estágios de Pipeline Gráficos**.  
  
 **Entrada do assembler**  
 O montador de entrada lê os dados de índice e vértice especificados pelo seu aplicativo e monta o hardware de gráficos.  
  
 Na janela estágios de Pipeline, a saída do Assembler de entrada é visualizada como um modelo de wireframe.  Para se examinar mais de perto o resultado, selecione **entrada Assembler** no **estágios de Pipeline gráficos** janela para exibir os vértices montados em 3D completo usando o Editor de modelo.  
  
> [!NOTE]
>  Se a semântica `POSITION` não estiver presente na saída do assembler de entrada, nada é exibido no estágio **Entrada do assembler**.  
  
 **Sombreador de vértice**  
 O estágio de sombreador de vértices processa vértices, normalmente executar operações como transformação, iluminação e capa.  Sombreadores de vértices produzem o mesmo número de vértices assume como entrada.  
  
 Na janela estágios de Pipeline, a saída do sombreador de vértices é visualizada como uma imagem de varredura de wireframe.  Para obter mais detalhadamente o resultado, selecione **sombreador de vértices** no **estágios de Pipeline gráficos** windows para exibir os vértices processados no Editor de imagem.  
  
> [!NOTE]
>  Se a semântica `POSITION` ou `SV_POSITION` não estiver presente na saída do sombreador de vértice, nada é exibido no estágio **Sombreador de Vértice**.  
  
 **Sombreador hull** \(Direct3D 11 e Direct3D apenas 12\)  
 Os processos de estágio de sombreador hull pontos que definem uma superfície de ordem inferior, como uma linha, triângulo ou quad de controle.  Como saída, ele produz um patch de geometria de ordem superior e constantes de patch que são passadas para o estágio de mosaico de funções fixas.  
  
 O estágio de sombreador hull não é visualizado na janela estágios de Pipeline.  
  
 **Tessellator estágio** \(Direct3D 11 e Direct3D apenas 12\)  
 O estágio de tessellator é uma unidade de hardware de função fixa \(não programável\) que pré\-processa o domínio representado pela saída do sombreador hull.  Como resultado, ele cria um padrão de amostragem do domínio e um conjunto de primitivos menores — pontos, linhas ou triângulos — que se conectam a esses exemplos.  
  
 O estágio de tessellator não é visualizado na janela estágios de Pipeline.  
  
 **Sombreador de domínio** \(Direct3D 11 e Direct3D apenas 12\)  
 O estágio de sombreador de domínio processa patches de geometria de ordem superior do sombreador Hull, fatores de mosaico juntos desde o estágio de mosaico.  O mosaico podem ser fatores incluem fatores de entrada tessellator, bem como fatores de saída.  Como resultado, ela calcula a posição de vértice de um ponto em que o patch de saída de acordo com os fatores de tessellator.  
  
 O estágio de sombreador de domínio não é visualizado na janela estágios de Pipeline.  
  
 **Sombreador de geometria**  
 O estágio de sombreadores de geometria processa todo primitivos — pontos, linhas ou triângulos — juntamente com os dados de vértice opcional primitivos adjacente a borda.  Ao contrário de sombreadores de vértices, recurso geometry shaders podem produzir mais ou menos primitivos que eles aceitam como entrada.  
  
 Na janela estágios de Pipeline, a saída do sombreador de geometria é visualizada como uma imagem de varredura de wireframe.  Para se examinar mais de perto o resultado, selecione **Geometry Shader** no **estágios de Pipeline gráficos** janela para exibir os primitivos de processado no Editor de imagem.  
  
 **Estágio de saída do fluxo**  
 O estágio de saída de fluxo pode interceptar primitivos transformados antes da rasterização e gravá\-las em memória. a partir daí os dados podem ser recirculated como entrada para o estágio anterior do pipeline gráfica ou ser lidos novamente pela CPU.  
  
 O estágio de output stream não é visualizado na janela estágios de Pipeline.  
  
 **Estágio rasterizador**  
 O estágio rasterizador é uma unidade de hardware \(não programável\) da função fixa que converte primitivos de vetor — pontos, linhas ou triângulos — em uma imagem de varredura executando a conversão de verificação de linha.  Durante a rasterização vértices são transformados no espaço do clipe homogêneo e recortados.  Como resultado, sombreadores de pixel são mapeados e atributos por vértice são interpolados entre o primitivo e preparados para o sombreador de pixel.  
  
 O estágio rasterizador não é visualizado na janela estágios de Pipeline.  
  
 **Sombreador de pixel**  
 Valores de pixel shader estágio processos varredura primitivos de junto com os dados de vértice interpolados para gerar por pixel como cores e a profundidade.  
  
 Na janela estágios de Pipeline, a saída do sombreador de pixel é visualizada como uma imagem de varredura colorido.  Para se examinar mais de perto o resultado, selecione **sombreador de Pixel** no **estágios de Pipeline gráficos** janela para exibir os primitivos de processado no Editor de imagem.  
  
 **Fusão de saída**  
 O estágio de output merger combina o efeito de pixels processados recentemente junto com o conteúdo existente de seus buffers correspondentes, cores, profundidade e estêncil — para gerar novos valores nesses buffers.  
  
 Na janela estágios de Pipeline, saída de fusão de saída é visualizada como uma imagem de varredura colorido.  Para analisar mais detalhadamente os resultados, selecione **Output Merger** no **estágios de Pipeline gráficos** janela para exibir o framebuffer mesclada.  
  
### Visualização do sombreador de vértices  
 Quando você seleciona o estágio de sombreador de vértice no **estágios de Pipeline gráficos** janela, o **Buffers de entrada** painel é exibido.  Aqui, você encontrará detalhes sobre a lista de vértices fornecido para o sombreador de vértices depois que elas foram reunidas pelo estágio de montador de entrada.  
  
 ![The vertex shader stage input buffer viewer](../debugger/media/gfx_diag_vertex_shader_inbuffers.png "gfx\_diag\_vertex\_shader\_inbuffers")  
  
 Para exibir o resultado do estágio de sombreador de vértices, escolha a miniatura do estágio de sombreador de vértices para exibir um tamanho máximo, wireframe varredura da malha após sua foram transformados pelo sombreador de vértices.  
  
 ![The vertex shader stage result preview](../debugger/media/gfx_diag_vertex_shader_preview.png "gfx\_diag\_vertex\_shader\_preview")  
  
## Consulte também  
 [Instruções passo a passo: objetos ausentes devido ao sombreamento de vértice](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Instruções passo a passo: depurando erros de renderização devido ao sombreamento](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)