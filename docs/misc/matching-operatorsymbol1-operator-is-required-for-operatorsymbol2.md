---
title: "Correspond&#234;ncia de &#39;&lt; operatorsymbol1 &gt;&#39; operador &#233; necess&#225;rio para &#39;&lt; operatorsymbol2 &gt;&#39; | Microsoft Docs"
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
  - "bc33033"
  - "vbc33033"
helpviewer_keywords: 
  - "BC33033"
ms.assetid: d2805e4f-08a8-4760-9539-565f51b88d13
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Correspond&#234;ncia de &#39;&lt; operatorsymbol1 &gt;&#39; operador &#233; necess&#225;rio para &#39;&lt; operatorsymbol2 &gt;&#39;
Um operador é definido quando o operador correspondente necessária não está definido.  
  
 Os operadores a seguir devem ser definidos como pares correspondentes:  
  
-   `=` e `<>`  
  
-   `>` e `<`  
  
-   `>=` e `<=`  
  
-   `IsTrue` e `IsFalse`  
  
 Se você definir qualquer um destes operadores em uma classe ou estrutura, você também deve definir o operador correspondente na mesma classe ou estrutura.  
  
 Mesmo que você não use o operador de correspondência explicitamente, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] pode precisar usá\-lo. Por exemplo, se você define uma classe ou estrutura que você usar como a variável de contador em um [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement), [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requer o `>=` e `<=` operadores \(bem como o `+` operador\).  
  
 **ID do erro:** BC33033  
  
### Para corrigir este erro  
  
-   Defina o operador de correspondência na mesma classe ou estrutura. Se esforçar para defini\-lo de forma significativa, porque [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] pode usá\-lo em uma situação em que você não pretende.  
  
## Consulte também  
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Como definir um operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Como definir um operador de conversão](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Operadores e expressões](/dotnet/visual-basic/programming-guide/language-features/operators-and-expressions/index)