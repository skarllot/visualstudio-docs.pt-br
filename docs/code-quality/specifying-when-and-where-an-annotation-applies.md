---
title: "Especificando quando e onde uma anota&#231;&#227;o se aplica | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Group_"
  - "_At_"
  - "_When_"
  - "_At_buffer_"
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Especificando quando e onde uma anota&#231;&#227;o se aplica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando uma anotação é condicional, pode exigir outras anotações especificar que o analisador.  Por exemplo, se uma função tem uma variável que pode ser síncrona ou assíncrona, a função se comporta como segue: Em caso síncrono sempre terá êxito se houver, mas os casos assíncronas reporta um erro se não ter imediatamente.  Quando a função é chamada de forma síncrona, verifique o valor do resultado não fornece nenhum valor ao analisador de código porque não retornaria.  No entanto, quando a função é chamada de forma assíncrona e o resultado da função não é verificado, um erro grave pode ocorrer.  Este exemplo ilustra uma situação em que você pode usar `_When_` anotação\- descrito posteriormente neste artigo permite verificar.  
  
## Anotações estruturais  
 Para controlar quando e onde as anotações se aplicam, use as anotações a seguir estruturais.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_At_(expr, anno-list)`|`expr` é uma expressão que gerencie um lvalue.  As anotações em `anno-list` são aplicadas ao objeto que é nomeada por `expr`.  Para cada anotação em `anno-list`, `expr` é interpretada em pré\-requisito se a anotação é interpretada na condição anterior, e pós\-atualização na condição se a anotação é interpretada em posteriores a condição.|  
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr` é uma expressão que gerencie um lvalue.  As anotações em `anno-list` são aplicadas ao objeto que é nomeada por `expr`.  Para cada anotação em `anno-list`, `expr` é interpretada em pré\-requisito se a anotação é interpretada na condição anterior, e pós\-atualização na condição se a anotação é interpretada em posteriores a condição.<br /><br /> `iter` é o nome de uma variável que é definir o escopo para a anotação \(inclusive de `anno-list`\).  `iter` tem um tipo `long`implícito.  As variáveis identicamente nomeados em qualquer escopo inclusive são ocultados de avaliação.<br /><br /> `elem-count` é uma expressão que é avaliada como um inteiro.|  
|`_Group_(anno-list)`|Todas as anotações em `anno-list` são consideradas ter qualquer qualificador que se aplicar à anotação de grupo que é aplicada a cada anotação.|  
|`_When_(expr, anno-list)`|`expr` é uma expressão que possa ser convertida em `bool`.  Quando for diferente de zero \(`true`\), as anotações especificadas em `anno-list` são consideradas aplicável.<br /><br /> Por padrão, para cada anotação em `anno-list`, `expr` é interpretado como usar os valores de entrada se a anotação é um pré\-requisito, e como usar os valores de saída se a anotação é uma condição pós\-instalação.  Para substituir a opção, você pode usar o intrínsecas de `_Old_` quando você avalia após uma condição para indicar que os valores de entrada devem ser usados. **Note:**  As anotações diferentes podem ser habilitadas no resultado de usar `_When_` se um mutável \- por exemplo, `*pLength`— estiver envolvido porque o resultado avaliado de `expr` na condição anterior pode ser diferente do resultado avaliado após na condição.|  
  
## Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código do C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Noções básicas de SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)   
 [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Funções intrínsecas](../code-quality/intrinsic-functions.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)