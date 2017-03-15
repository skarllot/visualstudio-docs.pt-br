---
title: "Tipo de &#39;&lt; variablename &gt;&#39; n&#227;o pode ser inferido de uma express&#227;o contendo &#39;&lt; variablename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30980"
  - "bc30980"
helpviewer_keywords: 
  - "BC30980"
ms.assetid: 43a5d008-5362-481b-845b-b9bb00a61a83
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de &#39;&lt; variablename &gt;&#39; n&#227;o pode ser inferido de uma express&#227;o contendo &#39;&lt; variablename &gt;&#39;
O compilador não pode inferir o tipo de dados de uma variável se a variável for usada em estabelecer o valor inicial na declaração.  
  
 Por exemplo, com `Option Infer` definido como `On`, não compilam os exemplos a seguir:  
  
-   Declarações  
  
    ```  
    ' Does not compile with Option Infer on. Dim m = m Dim d = someFunction(d)  
    ```  
  
-   `For` loop  
  
    ```  
    ' Does not compile with Option Infer on. For j = 1 To j Next  
    ```  
  
-   `For Each` loop  
  
    ```  
    ' Does not compile with Option Infer on. For Each customer In customer.Orders Next  
    ```  
  
 **ID do erro:** BC30980  
  
### Para corrigir este erro  
  
-   Se as duas variáveis pretendiam se referir a valores diferentes, altere o nome da variável que você está declarando.  
  
-   Use um valor literal em vez do nome de variável no valor inicial, no lado direito da atribuição.  
  
-   Use um `As` cláusula para especificar o tipo da variável que é declarado.  
  
## Consulte também  
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Instrução For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Inferência de tipo local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Instrução Option Infer](/dotnet/visual-basic/language-reference/statements/option-infer-statement)