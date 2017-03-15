---
title: "Resolu&#231;&#227;o sobrecarregada falhou porque nenhum &#39;&lt; m&#233;todo acess&#237;vel &gt;&#39; &#233; o mais espec&#237;fico para estes argumentos: &lt; erro &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30521"
  - "vbc30521"
helpviewer_keywords: 
  - "Falha de resolução"
  - "BC30521"
  - "Falha na resolução de sobrecarga"
ms.assetid: b8b41fa0-a64b-4e74-8443-be3afd2b6f11
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Resolu&#231;&#227;o sobrecarregada falhou porque nenhum &#39;&lt; m&#233;todo acess&#237;vel &gt;&#39; &#233; o mais espec&#237;fico para estes argumentos: &lt; erro &gt;
Você fez uma chamada para um método sobrecarregado, mas o compilador encontrou duas ou mais sobrecargas com listas de parâmetros para o qual a lista de argumentos pode ser convertida e ela não pode selecioná\-las.  
  
 O compilador tenta corresponder ao máximo os tipos de dados na lista de argumentos de chamada e a lista de parâmetros de sobrecarga. Ele requer uma conversão de ampliação de cada um de seus argumentos para o seu parâmetro correspondente, se a opção de verificação de tipo \([Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) é `On` ou `Off`.  
  
 Se o compilador encontrar mais de uma sobrecarga que satisfaça o requisito de ampliação, em seguida, procura a sobrecarga que é mais específica para os tipos de dados de argumento, ou seja, que chama o mínimo de ampliação. Ele gera essa mensagem de erro quando uma sobrecarga é mais específica para o tipo de dados de um argumento enquanto outra sobrecarga é mais específica para o tipo de dados do outro argumento. Para obter mais informações e um exemplo, consulte [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution).  
  
 **ID do erro:** BC30521  
  
### Para corrigir este erro  
  
1.  Examine todas as sobrecargas do método e determinar qual deles você deseja chamar.  
  
2.  Na sua declaração de chamada, verifique os tipos de dados dos argumentos correspondem aos tipos de dados dos parâmetros definidos para a sobrecarga desejada. Talvez você precise usar o [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function) para converter um ou mais tipos de dados para os tipos definidos.  
  
## Consulte também  
 [Sobrecarga de procedimento](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Considerações sobre procedimentos de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures)   
 [Resolução de sobrecarga](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)   
 [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Propriedades e métodos sobrecarregados](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function)