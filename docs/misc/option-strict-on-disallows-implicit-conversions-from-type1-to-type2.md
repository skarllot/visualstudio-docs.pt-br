---
title: "Option Strict On n&#227;o permite convers&#245;es impl&#237;citas de &#39;&lt; type1 &gt;&#39; para &#39;&lt; type2 &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30512"
  - "vbc30512"
helpviewer_keywords: 
  - "BC30512"
ms.assetid: b9756d48-05fa-4027-8a80-b4a0ef92099d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n&#227;o permite convers&#245;es impl&#237;citas de &#39;&lt; type1 &gt;&#39; para &#39;&lt; type2 &gt;&#39;
Você tentou converter um tipo em outro tipo que não poderá conter o valor, como um `Long` para um `Integer`, enquanto a opção de verificação de tipo \([Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)\) é definido como `On`.  
  
 Esse tipo de conversão é chamado um *conversão de redução*, e é possível que ele falhe em tempo de execução. Por esse motivo, `Option Strict On` não permite conversões de estreitamento implícitas.  
  
 **ID do erro:** BC30512  
  
### Para corrigir este erro  
  
1.  Determinar se há uma conversão de qualquer tipo do `<type1>` para `<type2>`. Se ambos estiverem [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tipos elementares, ou se ambos forem instâncias de classes, você geralmente pode fazer essa determinação consultando a tabela no [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions).  
  
2.  Se houver uma conversão de redução de apenas `<type1>` para `<type2>`, você deve usar a conversão explícita. O [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function) e [Operador DirectCast](/dotnet/visual-basic/language-reference/operators/directcast-operator) palavras\-chave acionar uma exceção de tempo de execução se a conversão falhar. O [Operador TryCast](/dotnet/visual-basic/language-reference/operators/trycast-operator) palavra\-chave se aplica somente aos tipos de referência e retorna [nada](/dotnet/visual-basic/language-reference/nothing) se a conversão falhar.  
  
3.  Se existe uma conversão de restrição e seu programa pode tolerar uma falha de tempo de execução, ou você tiver certeza de que uma falha de tempo de execução não é possível, você pode especificar `Option Strict Off` no início do seu código\-fonte. Mas você ainda deve colocar a conversão em um [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement) bloco para evitar resultados inesperados ou encerramento do programa.  
  
4.  Não se existir nenhuma conversão de `<type1>` para `<type2>`, você deve reavaliar sua lógica do programa. Você poderá escrever código que pode atribuir valores a serem `<type2>` correspondente previsto valores de `<type1>`.  
  
5.  Não se existir nenhuma conversão de `<type1>` para `<type2>` e um dos tipos é uma classe ou estrutura que você definiu, você poderá definir um operador de conversão de tipo para ou de outro tipo. Para obter mais informações, consulte [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md).  
  
6.  Em todos os casos e como diretriz geral, você deve evitar usar conversões de restrição, a menos que seja possível detectar falhas em um `Catch` Bloquear e lidar com eles de forma eficiente.  
  
## Consulte também  
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Função CType](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [Operador DirectCast](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [Operador TryCast](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [nada](/dotnet/visual-basic/language-reference/nothing)   
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)