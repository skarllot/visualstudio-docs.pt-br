---
title: "O tipo &#39;&lt; typename &gt;&#39; deve definir o operador &#39;&lt; operador &gt;&#39; a ser usado em uma instru&#231;&#227;o &#39;For&#39; | Microsoft Docs"
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
  - "vbc33038"
  - "BC33038"
helpviewer_keywords: 
  - "BC33038"
ms.assetid: b1c9d87f-80f9-4c8c-8908-f8400b9fe4c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; deve definir o operador &#39;&lt; operador &gt;&#39; a ser usado em uma instru&#231;&#227;o &#39;For&#39;
Um `For` loop Especifica uma variável de contador de um tipo que não oferece suporte a um operador necessário.  
  
 Variável de contador em um `For` loop pode ser de qualquer tipo de dados que oferece suporte a todos os operadores a seguir:  
  
-   Maior que ou igual \(`>=`\)  
  
-   Menor ou igual \(`<=`\)  
  
-   Adição \(`+`\)  
  
-   Subtração \(`-`\)  
  
 Se você usar um tipo de dados numéricos para a variável de contador, todos os operadores anteriores são compatíveis. Se você usar uma classe definida pelo usuário ou estrutura, você deve definir todos os operadores anteriores na classe ou estrutura.  
  
 Observe também que, tipos de dados do `start`, `end`, e `step` expressões no `For` instrução deve ampliar para o tipo de dados da variável de contador. Se a variável de contador é uma classe definida pelo usuário ou a estrutura e o `start`, `end`, ou `step` expressão é de um tipo diferente, você deve definir o `CType` operador de conversão para realizar a conversão necessária.  
  
 **ID do erro:** BC33038  
  
### Para corrigir este erro  
  
1.  Verifique a ortografia do tipo de dados de variável de contagem está correta.  
  
2.  Se você estiver usando uma classe definida pelo usuário ou estrutura para a variável de contador, defina todos os operadores na classe ou estrutura.  
  
3.  Dependendo dos tipos de dados do `start`, `end`, e `step` expressões, você talvez precise definir uma ou mais `CType` operadores de conversão para convertê\-los para o tipo de dados da variável de contador.  
  
## Consulte também  
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function)