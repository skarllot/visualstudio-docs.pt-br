---
title: "O operando &#39;Throw&#39; deve derivar de &#39;System. Exception&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30665"
  - "bc30665"
helpviewer_keywords: 
  - "BC30665"
ms.assetid: 7c228087-39ea-4b30-a410-6ba711e67e5e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O operando &#39;Throw&#39; deve derivar de &#39;System. Exception&#39;
O argumento fornecido para `Throw` deve ser uma instância de `System.Exception` ou uma instância de uma classe derivada de `System.Exception`.  
  
 **ID do erro:** BC30665  
  
### Para corrigir este erro  
  
-   Use um argumento derivado de `System.Exception`, como no exemplo a seguir.  
  
    ```  
    Throw New System.Exception("This is an error.")  
    ```  
  
## Consulte também  
 [Instrução Throw](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Classe de exceção no Visual Basic](http://msdn.microsoft.com/pt-br/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Exceção e tratamento de erros no Visual Basic](http://msdn.microsoft.com/pt-br/3e351e73-cf23-40ab-8b60-05794160529e)