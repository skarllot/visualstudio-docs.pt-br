---
title: "Anotando o comportamento da fun&#231;&#227;o | Microsoft Docs"
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
  - "_On_failure_"
  - "_Return_type_success_"
  - "_Always_"
  - "_Maybe_raises_SEH_exception_"
  - "_Raises_SEH_exception_"
  - "_Called_from_function_class_"
  - "_Function_class_"
  - "_Must_inspect_result_"
  - "_Success_"
  - "_Check_return_"
  - "_Use_decl_annotations_"
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Anotando o comportamento da fun&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Além de efetuar [parâmetros e valores de retorno da função](../code-quality/annotating-function-parameters-and-return-values.md), é possível anotar propriedades de função inteiro.  
  
## Anotações de função  
 As anotações a seguir se aplicam à função no conjunto e descrevem como se comporta ou o espera que seja verdadeira.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_Called_from_function_class_(name)`|Não é destinado apenas estar; em vez disso, é um predicado a ser usado com a anotação de `_When_` .  Para obter mais informações, consulte [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> O parâmetro de `name` é uma cadeia de caracteres arbitrária que também aparece em uma anotação de `_Function_class_` na declaração de algumas funções.  retorna `_Called_from_function_class_` diferente de zero se a função que está sendo analisado é atualmente anotada usando `_Function_class_` que tem o mesmo valor de `name`; caso contrário, retorna zero.|  
|`_Check_return_`|Anota um valor de retorno e indica que o chamador deve inspecionar o.  O verificador reporta um erro se a função é chamada em um contexto nulo.|  
|`_Function_class_(name)`|O parâmetro de `name` é uma cadeia de caracteres arbitrária que é designada pelo usuário.  Existir em um namespace que é diferente de outros namespaces.  Uma função, um ponteiro de função, ou \- mais um tipo de ponteiro da função de usefully\-a podem ser designados como pertencendo a uma ou mais classes da função.|  
|`_Raises_SEH_exception_`|Anota uma função que eleva sempre uma exceção estruturado \(SEH\) de manipulador de exceção, sujeito à `_When_` e as condições de `_On_failure_` .  Para obter mais informações, consulte [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
|`_Maybe_raises_SEH_exception_`|Anota uma função que pode opcionalmente aumentar a exceção, sujeita a `_When_` e condições de `_On_failure_` .|  
|`_Must_inspect_result_`|Anota qualquer valor de saída, inclusive o valor de retorno, os parâmetros, e os globais.  O analisador relatará um erro se o valor do objeto anotado não é inspecionado subsequentemente. A “inspeção” inclui se for usada em uma expressão condicional, atribuída a um parâmetro de saída ou global, ou é passado como um parâmetro.  Para valores de retorno, `_Must_inspect_result_` implica `_Check_return_`.|  
|`_Use_decl_annotations_`|Pode ser usado em uma definição de função \(também conhecida como um corpo de função\) em lugar da lista de anotações no cabeçalho.  Quando `_Use_decl_annotations_` for usado, as anotações que aparecem em um cabeçalho em escopo para a mesma função são usadas como se também estão presentes na definição que tem a anotação de `_Use_decl_annotations_` .|  
  
## Anotações de êxito\/reprovado  
 Uma função pode falhar, e quando fizer isso, os resultados podem estar incompletos ou diferir dos resultados quando a função tenha êxito.  As anotações na lista a seguir fornecem modos para expressar o comportamento da falha.  Para usar essas anotações, é necessário habilitá\-los para determinar o êxito; em virtude disso, uma anotação de `_Success_` é necessária.  Observe que `NTSTATUS` e `HRESULT` já têm uma anotação de `_Success_` compilada neles; no entanto, se você especificar sua própria anotação de `_Success_` em `NTSTATUS` ou em `HRESULT`, substitui a anotação interno.  
  
|Anotação|Descrição|  
|--------------|---------------|  
|`_Always_(anno_list)`|Equivalente a `anno_list _On_failure_(anno_list)`; ou seja, as anotações em `anno_list` se aplicam mesmo que a função tenha êxito.|  
|`_On_failure_(anno_list)`|Para ser usado apenas quando `_Success_` também é usado para anotar explicitamente o com um ou outro, ou implicitamente com `_Return_type_success_` em um typedef.  Quando a anotação de `_On_failure_` presentes em um parâmetro ou um valor de retorno da função, cada anotação em `anno_list` \(anno\) se comportará como se foi codificado como `_When_(!expr, anno)`, onde `expr` é o parâmetro à anotação necessária de `_Success_` .  Isso significa que o aplicativo indicado de `_Success_` após a todas as condições não se aplica a `_On_failure_`.|  
|`_Return_type_success_(expr)`|Pode ser aplicado ao typedef.  Indica que todas as funções que retornam esse tipo e não têm explicitamente `_Success_` são anotadas como se tivessem `_Success_(expr)`.  `_Return_type_success_` não pode ser usada em uma função ou um typedef do ponteiro de função.|  
|`_Success_(expr)`|`expr` é uma expressão que gerencie um rvalue.  Quando a anotação de `_Success_` está presente em uma declaração ou em uma definição de função, cada`anno`anotação \(\) na função e pós\-atualização na condição se comportará como se foi codificada como `_When_(expr, anno)`.  A anotação de `_Success_` pode ser usada apenas em uma função, não na parâmetros ou tipo de retorno.  Pode haver no máximo uma anotação de `_Success_` em uma função, e não pode estar em qualquer `_When_`, em `_At_`, ou em `_Group_`.  Para obter mais informações, consulte [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md).|  
  
## Consulte também  
 [Usando anotações de SAL para reduzir defeitos de código do C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Noções básicas de SAL](../code-quality/understanding-sal.md)   
 [Anotando parâmetros de função e valores de retorno](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Anotando estruturas e classes](../code-quality/annotating-structs-and-classes.md)   
 [Anotando o comportamento de bloqueio](../code-quality/annotating-locking-behavior.md)   
 [Especificando quando e onde uma anotação se aplica](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funções intrínsecas](../code-quality/intrinsic-functions.md)   
 [Práticas recomendadas e exemplos](../code-quality/best-practices-and-examples-sal.md)