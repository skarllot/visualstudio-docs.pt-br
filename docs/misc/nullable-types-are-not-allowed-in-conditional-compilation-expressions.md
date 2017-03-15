---
title: "Tipos anul&#225;veis n&#227;o s&#227;o permitidos em express&#245;es de compila&#231;&#227;o condicional | Microsoft Docs"
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
  - "bc33111"
  - "vbc33111"
helpviewer_keywords: 
  - "BC33111"
ms.assetid: 2c2587e5-2179-4a31-bcf7-7004db6f2d73
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipos anul&#225;veis n&#227;o s&#227;o permitidos em express&#245;es de compila&#231;&#227;o condicional
Um tipo anulável não pode ser usado na expressão de uma diretiva de compilação condicional. Por exemplo, o código a seguir causa esse erro.  
  
```vb#  
'#Const triggerPoint = 0 '' Not valid. '#If CType(triggerpoint, Boolean?) = True Then '        ' Body of the conditional directive. '#End If  
```  
  
 **ID do erro:** BC33111  
  
### Para corrigir este erro  
  
-   Remova a designação de tipo anulável.  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Diretivas \#If...Then...\#Else](/dotnet/visual-basic/language-reference/directives/if-then-else-directives)   
 [Compilação condicional](/dotnet/visual-basic/programming-guide/program-structure/conditional-compilation)