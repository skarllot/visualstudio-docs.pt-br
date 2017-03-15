---
title: "Fun&#231;&#245;es intr&#237;nsecas | Microsoft Docs"
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
  - "_String_length_"
  - "_Param_"
  - "_Curr_"
  - "_Old_"
  - "_Nullterm_length_"
  - "_Inexpressible_"
ms.assetid: adf29f8c-89fd-4a5e-9804-35ac83e1c457
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Fun&#231;&#245;es intr&#237;nsecas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Uma expressão em SAL pode ser expressão c \/C criando contanto que é uma expressão que não tenha o lado efeito\- por exemplo, criando \-\-, e todas as chamadas de função têm efeitos colaterais neste contexto.  No entanto, o SAL fornece qualquer função como os objetos e alguns símbolos reservadas que podem ser usados em expressões de SAL.  Esses são referidas como *funções intrínsecas*.  
  
## Uso geral  
 As anotações a seguir instrinsic de função fornecem o utilitário geral do SAL.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_Curr_`|Um sinônimo para o objeto que está sendo anotado atualmente.  Quando a anotação de `_At_` estiver em uso, `_Curr_` é o mesmo que o primeiro parâmetro para `_At_`.  Caso contrário, será o parâmetro ou a função inteira\/valor de retorno com que a anotação é associada léxica.|  
|`_Inexpressible_(expr)`|Para expressar uma situação em que o tamanho de um buffer é muito complexa representar usando uma anotação expressão para o exemplo, quando é computado por meio do exame de um conjunto de dados de entrada e depois contando membros selecionados.|  
|`_Nullterm_length_(param)`|`param` é o número de elementos no buffer até mas não incluindo um terminador nulo.  Pode ser aplicado a qualquer buffer de não agregação, o tipo não nulo.|  
|`_Old_(expr)`|Quando é avaliado na condição anterior, `_Old_` retorna o valor de entrada `expr`.  Quando é avaliado na condição pós\-instalação, retorna o valor `expr` porque seria avaliada em pré\-requisito.|  
|`_Param_(n)`|O º parâmetro de `n`a uma função, contando de 1 a `n`, e `n` integral é uma constante literal.  Se o parâmetro for, esta anotação é idêntica a acessar o parâmetro por nome. **Note:**  `n` pode consultar os parâmetros posicionais que são definidos pelas reticências, ou pode ser usado em protótipos de função em que os nomes não são usados.|  
|`return`|A palavra\-chave reservada C\/C\+\+ `return` pode ser usado em uma expressão de SAL para indicar o valor de retorno de uma função.  O valor está disponível somente no estado da postagem; é um erro de sintaxe para usá\-lo pre no estado.|  
  
## Específico de cadeia de caracteres  
 As anotações a seguir da função intrínseca habilitam a manipulação de cadeias de caracteres.  Todos os quatro dessas funções oferecem a mesma finalidade: para retornar o número de elementos do tipo que é encontrado antes de um terminador nulo.  As diferenças são os tipos de dados em elementos que são referenciados.  Observe que se você deseja especificar o comprimento de um buffer com terminação nula que não é composto de caracteres, use a anotação de `_Nullterm_length_(param)` da seção anterior.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_String_length_(param)`|`param` é o número de elementos na cadeia de caracteres até mas não incluindo um terminador nulo.  Essa anotação é reservada para tipos de cadeia de caracteres de caractere.|  
|`strlen(param)`|`param` é o número de elementos na cadeia de caracteres até mas não incluindo um terminador nulo.  Essa anotação é reservada para uso em matrizes de caractere e é semelhante à função [strlen \(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)de tempo de execução C.|  
|`wcslen(param)`|`param` é o número de elementos na cadeia de caracteres até \(mas não incluindo\) em um terminador nulo.  Essa anotação é reservada para uso em matrizes de caracteres amplas e é semelhante à função [wcslen \(\)](/visual-cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l)de tempo de execução C.|  
  
## Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código do C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Noções básicas de SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando o comportamento da função](../code-quality/annotating-function-behavior.md)   
 [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)