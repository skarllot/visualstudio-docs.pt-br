---
title: "Trabalhando com texturas e imagens | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fbc8fa-66d1-4055-8460-24d8b8fbe43e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Trabalhando com texturas e imagens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar o Editor de imagens em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para criar e modificar texturas e imagens. O Editor de imagem oferece suporte aos formatos avançados de textura e imagens como aqueles que são usados no desenvolvimento de aplicativos do DirectX.  
  
> [!NOTE]
>  O Editor de imagens não oferece suporte a imagens de baixa cores como ícones ou cursores. Para criar ou modificar esses tipos de imagens, use o [Editor de imagens para ícones](/visual-cpp/windows/image-editor-for-icons).  
  
## Texturas e imagens  
 Texturas e imagens são, em um nível básico, apenas tabelas de dados que são usados para fornecer detalhes em aplicativos de gráficos. O tipo de detalhe que fornece uma imagem ou textura depende de como ele é usado, mas valores de altura, valores de alfa \(transparência\), normais da superfície e amostras de cor são exemplos comuns. A principal diferença entre uma textura e uma imagem é que uma textura deve ser usado junto com uma representação de forma — normalmente um modelo 3D — expressar um objeto completo ou cena, mas uma imagem é normalmente uma representação independente do objeto ou cena.  
  
 Tipos comuns de texturas incluem:  
  
 Mapas de textura  
 Mapas de textura contêm valores de cor que são organizados como uma uma, duas ou matriz tridimensional. Eles são usados para fornecer detalhes de cor no objeto afetado. Cores normalmente são codificadas usando os canais de cor RGB \(vermelho, verde, azul\) e pode incluir uma quarta canal, alfa, que representa a transparência. Menor frequência, cores poderiam ser codificadas em outro esquema de cores, ou o quarto canal pode conter dados que não seja alfa — por exemplo, a altura.  
  
 Mapas normais  
 Mapas normais contêm normais da superfície. Eles são usados para fornecer detalhes de iluminação no objeto afetado. Normals normalmente são codificados usando os componentes de cor vermelho, verde e azul para armazenar os x, y e dimensões de z do vetor. No entanto, existem outras codificações — por exemplo, codificações baseados em coordenadas polares.  
  
 Mapas de altura  
 Mapas de altura contêm dados de campo de altura. Eles são usados para fornecer um formulário de detalhe Geométrico no objeto afetado — usando o código do sombreador para calcular o efeito desejado, ou para fornecer pontos de dados para fins como geração de terreno. Valores de altura normalmente são codificados usando um canal em uma textura.  
  
 Mapas de cubo  
 Mapas de cubo podem conter diferentes tipos de dados — por exemplo, cores ou normais, mas são organizados como seis texturas nas faces de um cubo. Por causa disso, mapas de cubo não são amostrados fornecendo as coordenadas de textura, mas fornecendo um vetor cuja origem é o centro do cubo; o exemplo é capturado no ponto onde o vetor cruza o cubo. Mapas de cubo são usados para fornecer uma aproximação do ambiente que pode ser usado para calcular os reflexos — isso é conhecido como *mapeamento ambiente*— ou para fornecer textura a objetos esféricas menos distorção do basic, texturas bidimensionais podem fornecer.  
  
 Qualquer textura pode ser codificada e compactada em um número de maneiras que estão ortogonais para o tipo de dados que contém uma textura, ou a dimensionalidade ou "forma" da textura. No entanto, os métodos de compactação e codificação diferente produzem resultados melhores para diferentes tipos de dados.  
  
 Você pode usar o Editor de imagens para criar e modificar texturas e imagens de maneiras semelhantes a outros editores de imagem. O Editor de imagens também fornece Mapeamento mip e outros recursos para uso com elementos gráficos 3D e oferece suporte a muitos dos formatos de textura altamente compactados, acelerada por hardware que oferece suporte ao DirectX.  
  
## Tópicos relacionados  
  
|Título|Descrição|  
|------------|---------------|  
|[Editor de Imagem](../designers/image-editor.md)|Descreve como usar o Editor de imagens para trabalhar com texturas e imagens.|  
|[Exemplos do Editor de Imagem](../designers/image-editor-examples.md)|Fornece links para tópicos que demonstram como usar o Editor de imagens para executar tarefas de processamento de imagens comuns.|