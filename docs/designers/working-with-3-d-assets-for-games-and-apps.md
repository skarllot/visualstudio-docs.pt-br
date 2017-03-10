---
title: "Trabalhando com ativos 3D para jogos e aplicativos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics"
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 24
caps.handback.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Trabalhando com ativos 3D para jogos e aplicativos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse documento descreve as [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ferramentas que você pode usar para criar ou modificar modelos, texturas e sombreadores 3D para jogos e aplicativos baseados em DirectX.  
  
## Desenvolvimento de aplicativo DirectX no Visual Studio  
 Um aplicativo DirectX combina geralmente a lógica de programação, o API do DirectX e programas de Alto Nível de Language de Sombreamento \(HLSL\), juntamente com recursos visuais e de áudio 3\-D para apresentar uma experiência de multimídia interativa rica.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inclui ferramentas que você pode usar para trabalhar com imagens e texturas, modelos 3D, e sombreadores sem deixar de usar o IDE para usar outra ferramenta.  As ferramentas do Visual Studio são adequadas principalmente para criar os recursos *de espaço reservado* , que você pode usar para testar o código ou compilar protótipos antes de autorizar recursos prontos para produção, e para inspecionar e alterar os recursos prontos para produção quando estiver depurando o aplicativo.  
  
 Aqui está mais informações sobre os tipos de recursos que você pode trabalhar com o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Imagens e texturas  
 Imagens e texturas fornecem a cor e o detalhe visual em jogos e aplicativos.  Em gráficos 3\-D, texturas vêm em uma variedade de formatos, tipos, e geometrias para suportar usos diferentes.  Por exemplo, os mapeamentos normais fornecem normais de superfície por pixel para iluminação mais detalhada de modelos 3\-D e os mapeamentos de cubo fornecem a textura em todas as direções para usos como o caixas no céu, reflexos e mapeamento de textura esférica.  As texturas podem fornecer mapas mip para suportar a renderização eficiente em diferentes níveis de detalhes e podem suportar os canais de cor diferentes e os pedidos de cor.  As texturas podem ser armazenadas em uma variedade de formatos compactados que ocupam menos memória de gráficos exclusivo e ajuda os GPUS a acessar as texturas com mais eficiência.  
  
 Você pode usar o editor de imagem de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabalhar com imagens e texturas de muitos tipos e formatos comuns.  
  
### Modelos 3\-D  
 Os modelos 3\-D criam espaço e forma em jogos e aplicativos.  Minimamente, os modelos codificam a posição dos pontos no espaço 3\-D \- que são conhecidas como *vértices*\- junto com os dados de indexação para definir as linhas ou os triângulos que representam a forma do modelo.  Os dados adicionais podem ser associados à esses vértices \- por exemplo, informações de cores, vetores normais ou atributos específicos do aplicativo.  Cada modelo também pode definir atributos em todo objeto \- por exemplo, o sombreador usado para calcular a aparência da superfície do objeto ou em qual textura é aplicada.  
  
 Você pode usar o editor de modelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabalhar com modelos 3D em vários formatos comuns.  
  
### Sombreadores  
 Os sombreadores são pequenos programas específicos de domínios que são executados na unidade de processamento gráfico \(GPU\).  Os sombreadores determinam como os modelos 3D são transformados em formas na tela e como cada pixel nessas formas é colorido.  Criando um sombreador e aplicando\-o a um objeto no seu jogo ou aplicativo, você pode dar ao objeto uma aparência exclusiva.  
  
 Você pode usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Shader Designer, que é uma ferramenta de design de sombreador com base em elementos gráficos, para criar efeitos visuais personalizados sem conhecer a programação de HLSL.  
  
> [!NOTE]
>  Para obter mais informações sobre como iniciar com DirectX que programa, consulte [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633).  Para obter mais informações sobre como depurar um aplicativo baseado em DirectX, consulte [Diagnóstico de gráficos \(depurando gráficos DirectX\)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## Compatibilidade de versão de DirectX  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa DirectX para recursos de renderização 2D e 3D.  Você pode selecionar o renderizador de DirectX 11, ou o renderizador avançado de software do windows \(WARP\) da plataforma de Renderização.  O renderizador DirectX 11 fornece uma renderização de alto desempenho acelerada pelo hardware em GPUs DirectX 11 e DirectX 10.  O renderizador WARP ajuda a garantir que seus ativos funcionam com uma ampla gama de computadores — isso inclui computadores que não possuem hardware gráfico modernos e computadores que integraram o hardware gráfico.  Para obter mais informações sobre a URDIDURA, consulte [Guia avançado do windows \(WARP\) da plataforma de Rasterization](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## Tópicos relacionados  
  
|Nome|Descrição|  
|----------|---------------|  
|[Trabalhando com texturas e imagens](../designers/working-with-textures-and-images.md)|Descreve como usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabalhar com imagens e texturas.|  
|[Trabalhando com modelos 3D](../designers/working-with-3-d-models.md)|Descreve como usar o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabalhar com modelos 3\-D.|  
|[Trabalhando com sombreadores](../designers/working-with-shaders.md)|Descreve como usar o Shader Designer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para criar e modificar efeitos de sombreamento personalizados.|  
|[Usando ativos 3D no jogo ou no aplicativo](../designers/using-3-d-assets-in-your-game-or-app.md)|Descreve como usar os recursos, que você criou usando o Editor de Imagem, o Editor Modelo ou Shader Designer no seu jogo ou aplicativo.|