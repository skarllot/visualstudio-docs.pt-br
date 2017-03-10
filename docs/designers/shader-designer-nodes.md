---
title: "N&#243;s do Designer de Sombreador | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f5192fbd-c78f-40a8-a4d4-443209610268
caps.latest.revision: 6
caps.handback.revision: 6
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# N&#243;s do Designer de Sombreador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Os artigos nesta seção de documentação contêm informações sobre os vários nós do Shader Designer que você pode usar para criar efeitos gráficos.  
  
## Nós e tipos de nó  
 O Design de Sombreador representa efeitos visuais como um gráfico.  Esses elementos gráficos são compilados a partir de nós escolhidos especificamente e conectados de formas precisas para obter a influência pretendida.  Cada nó representa um fragmento de informação ou uma função matemática e as conexões entre elas representam como as informações fluem através do gráfico para gerar o resultado.  O Shader Designer fornece seis tipos diferentes de nó — filtros, nós de textura, parâmetros, constantes, nós utilitárias e nós matemáticos — e vários nós individuais pertencem a cada tipo.  Esses nós e tipos de nós são descritos em outros artigos nessa seção — consulte os links no final deste documento.  
  
## Estrutura do nó  
 Todos os nós são compostos de uma combinação de elementos comuns.  Cada nó tem pelo menos um terminal de saída no lado direito \(exceto o nó de cor final, que representa a saída do sombreador\).  Os nós que representam cálculos ou exemplos de textura possuem terminais de entrada à esquerda, mas os nós que representam informações não possuem terminais de entrada.  Os terminais de saída são conectados aos terminais de entrada para que as informações sejam movidas de um nó para outro.  
  
### Promoção de entradas  
 Como o Shader Designer finalmente deve gerar o código\-fonte HLSL de modo que o efeito possa ser usado em um jogo ou aplicativo, os nós do Shader Designer estão sujeitos a promoção de tipos que usa regras HLSL.  Como o hardware gráfico opera primeiro em valores de ponto flutuante, a promoção de tipos entre tipos diferentes \- por exemplo, de `int` para `float` ou de `float` para `double`— é incomum.  Em vez disso, porque o hardware de gráficos usa a mesma operação em várias partes de informação de uma vez, um tipo diferente de promoção pode ocorrer em que o menor número de entradas é alongada para corresponder com o tamanho da entrada maior.  Como o alongamento depende do tipo de entrada e também da própria operação:  
  
-   **Se o tipo menor é um valor escalar, então:**  
  
     O valor escalar é replicado em um vetor de tamanho igual à maior entrada.  Por exemplo, a entrada escalar 5.0 se torna o vetor \(5.0, 5.0, 5.0\) quando a maior entrada da operação é um vetor de três elemento, independente da operação.  
  
-   **Se o tipo menor é um vetor, e a operação é multiplicativa \(\*, \/, %, e assim por diante\), então:**  
  
     O valor vetorial é copiado nos principais elementos de um vetor de igual tamanho à maior entrada, e os elementos à direita são definidos como 1.0.  Por exemplo, a entrada do vetor \(5.0, 5.0\) se torna o vetor \(5.0, 5.0, 1.0, 1.0\) quando é multiplicado por um vetor de quatro elementos.  Isso preserva o terceiro e o quarto elemento da saída usando a identidade multiplicativa, 1.0.  
  
-   **Se o tipo menor é um vetor, e a operação é aditiva \(\+, \-, e assim por diante\), então:**  
  
     O valor vetorial é copiado nos principais elementos de um vetor que é igual em tamanho à entrada maior e os elementos à direita são definidos para 0,0.  Por exemplo, a entrada do vetor \(5.0, 5.0\) se torna o vetor \(5.0, 5.0, 0.0, 0.0\) quando é adicionado a um vetor de quatro elementos.  Isso preserva o terceiro e o quarto elemento da saída usando a identidade aditiva, 0.0.  
  
## Tópicos relacionados  
  
|Nome|Descrição|  
|----------|---------------|  
|[Nós de constante](../designers/constant-nodes.md)|Descreve os nós que você pode usar para representar valores literais e informações de estado de vértice interpolada em cálculos do sombreador.  Como o estado do vértice é interpolado \- e portanto, é diferente para cada pixel \- cada instância do sombreador de pixel recebe uma versão diferente da constante.|  
|[Nós de parâmetro](../designers/parameter-nodes.md)|Descreve os nós que você pode usar para representar a posição da câmera, propriedades de material, parâmetros de iluminação, hora e outras informações de estado de aplicativo em cálculos do sombreador.|  
|[Nós de textura](../designers/texture-nodes.md)|Descreve os nós que você pode usar para provar vários tipos de textura e geometria e para produzir ou transformar coordenadas de textura de maneiras comuns.|  
|[Nós de matemática](../designers/math-nodes.md)|Descreve os nós que você pode usar para executar algébrico, lógica, trigonométricas e outras operações matemáticas que mapeiam diretamente para as instruções HLSL.|  
|[Nós de utilitário](../designers/utility-nodes.md)|Descreve os nós que você pode usar para executar cálculos de iluminação comuns e outras operações comuns que não mapeiam diretamente para as instruções HLSL.|  
|[Filtrar nós](../designers/filter-nodes.md)|Descreve os nós que você pode usar para executar a filtragem de textura e de cor.|