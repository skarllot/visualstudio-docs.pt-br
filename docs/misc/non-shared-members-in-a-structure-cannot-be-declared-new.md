---
title: "Membros n&#227;o compartilhados em uma estrutura n&#227;o podem ser declarados como &#39;New&#39; | Microsoft Docs"
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
  - "vbc30795"
  - "BC30795"
helpviewer_keywords: 
  - "BC30795"
ms.assetid: 8e4e1ad8-3bac-475f-82e8-e4f134692204
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Membros n&#227;o compartilhados em uma estrutura n&#227;o podem ser declarados como &#39;New&#39;
Uma variável não compartilhada em uma estrutura é declarada com um `New` cláusula.  
  
 Você pode inicializar uma variável de referência compartilhada em uma estrutura, e você pode ter uma variável de referência não compartilhada sem inicialização, como as seguintes linhas de código mostram.  
  
 `Shared structVar1 As New System.ApplicationException`  
  
 `Dim structVar2 As System.ApplicationException`  
  
 No entanto, você não pode inicializar uma variável de referência não compartilhada em uma estrutura. A linha de código a seguir é inválida.  
  
 `Dim structVar3 As New System.ApplicationException ' INVALID IN A STRUCTURE`  
  
 **ID do erro:** BC30795  
  
### Para corrigir este erro  
  
-   Remova o `Shared` modificador ou `New` palavra\-chave da declaração da variável de referência.  
  
## Consulte também  
 [Instrução Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Compartilhado](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [Operador New](/dotnet/visual-basic/language-reference/operators/new-operator)