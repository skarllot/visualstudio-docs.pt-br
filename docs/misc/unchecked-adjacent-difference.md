---
title: "unchecked_adjacent_difference | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.unchecked_adjacent_difference"
  - "std::unchecked_adjacent_difference"
  - "unchecked_adjacent_difference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Função unchecked_adjacent_difference"
ms.assetid: 3a6b0b49-a84b-40b1-bcd5-3bf76c6ef7d7
caps.latest.revision: 14
caps.handback.revision: 14
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
---
# unchecked_adjacent_difference
Mesmo que [adjacent\_difference](../Topic/adjacent_difference.md), mas permite o uso de um iterador não verificado como iterador de saída quando secure\_scl \= 1 é definido.`unchecked_adjacent_difference` é definido na `stdext` namespace.  
  
> [!NOTE]
>  Esse algoritmo é uma extensão da Microsoft à biblioteca C\+\+ padrão. O código implementado usando esse algoritmo não será portátil.  
  
## Sintaxe  
  
```  
template<class InputIterator, class OutIterator>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result   
   );  
  
template<class InputIterator, class OutputIterator, class BinaryOperation>  
   OutputIterator unchecked_adjacent_difference(  
      InputIterator_First,  
      InputIterator _Last,  
      OutputIterator_Result,   
      BinaryOperation _Binary_op  
   );  
```  
  
#### Parâmetros  
 `_First`  
 Um iterador de entrada que trata o primeiro elemento no intervalo de entrada cujos elementos deverão ser diferenciados com seus respectivos antecessores ou onde o par de valores deve ser operado por qualquer outra operação binária especificada.  
  
 `_Last`  
 Um iterador de entrada que trata o último elemento no intervalo de entrada cujos elementos deverão ser diferenciados com seus respectivos antecessores ou onde o par de valores deve ser operado por qualquer outra operação binária especificada.  
  
 `_Result`  
 Um iterador de saída que trata o primeiro elemento de um intervalo de destino onde a série de diferenças ou os resultados da operação especificada a ser armazenado.  
  
 `_Binary_op`  
 A operação binária que deve ser aplicada na operação generalizada substituindo a operação de subtração no procedimento de diferenciação.  
  
## Valor de retorno  
 Um iterador de saída que trata o final do intervalo de destino: `_Result` \+ \(`_Last` \- `_First`\).  
  
## Comentários  
 Consulte [adjacent\_difference](../Topic/adjacent_difference.md) para obter um exemplo de código.  
  
 Para obter mais informações sobre iteradores verificados, consulte [Iteradores Verificados](/visual-cpp/standard-library/checked-iterators).  
  
## Requisitos  
 **Cabeçalho:** \< numeric \>  
  
 **Namespace:** stdext  
  
## Consulte também  
 [Biblioteca de Modelos Padrão](../misc/standard-template-library.md)