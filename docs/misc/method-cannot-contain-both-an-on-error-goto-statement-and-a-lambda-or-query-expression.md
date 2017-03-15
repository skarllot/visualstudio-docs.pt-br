---
title: "O m&#233;todo n&#227;o pode conter uma instru&#231;&#227;o &#39;On Error GoTo&#39; e uma express&#227;o lambda ou de consulta | Microsoft Docs"
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
  - "bc36595"
  - "vbc36595"
helpviewer_keywords: 
  - "BC36595"
ms.assetid: 4e7cc11e-f53d-4481-afb4-653a81d54483
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O m&#233;todo n&#227;o pode conter uma instru&#231;&#227;o &#39;On Error GoTo&#39; e uma express&#227;o lambda ou de consulta
Um método contém um `On Error Goto` instrução e uma expressão lambda ou uma consulta LINQ. Você não pode incluir um `On Error Goto` instrução com uma expressão lambda ou consulta LINQ em um método.  
  
 **ID do erro:** BC36595  
  
### Para corrigir este erro  
  
1.  Substitua a código que usa de manipulação de exceção de `On Error Goto` instrução com um `Try...Catch` instrução.  
  
## Consulte também  
 [Introdução à exceção tratamento \(Visual Basic\)](http://msdn.microsoft.com/pt-br/9792f16a-0cd2-40bd-ace2-f7a4344c0e52)   
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Introdução a LINQ no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [Expressões lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Instrução On Error](/dotnet/visual-basic/language-reference/statements/on-error-statement)