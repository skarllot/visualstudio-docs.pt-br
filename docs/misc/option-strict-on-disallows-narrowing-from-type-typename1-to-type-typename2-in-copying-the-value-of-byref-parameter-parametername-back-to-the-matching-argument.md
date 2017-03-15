---
title: "Option Strict On n&#227;o permite restringir do tipo &#39;&lt; typename1 &gt;&#39; tipo &#39;&lt; typename2 &gt;&#39; ao copiar o valor do par&#226;metro ByRef &lt; parametername &gt;&#39; para o argumento correspondente | Microsoft Docs"
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
  - "bc32029"
  - "vbc32029"
helpviewer_keywords: 
  - "BC32029"
ms.assetid: fc9ae5d2-b506-47cf-a50c-116fda5ed206
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On n&#227;o permite restringir do tipo &#39;&lt; typename1 &gt;&#39; tipo &#39;&lt; typename2 &gt;&#39; ao copiar o valor do par&#226;metro ByRef &lt; parametername &gt;&#39; para o argumento correspondente
Fornece uma chamada de procedimento um `ByRef` argumento com um tipo de dados que amplia para o argumento do tipo declarado, e `Option Strict` é `On`. A conversão widening é permitida quando o argumento é passado para o procedimento, mas quando o procedimento modifica o conteúdo do argumento variável no código de chamada, a conversão inversa é restringir. Conversões de restrição não são permitidas com `Option Strict On`.  
  
 **ID do erro:** BC32029  
  
### Para corrigir este erro  
  
-   Fornecer cada `ByRef` argumento no procedimento de chamada com o mesmo tipo de dados como o tipo declarado ou ativar `Option Strict Off`.  
  
## Consulte também  
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Passando argumentos por valor e por referência](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Conversões implícitas e explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)