---
title: "CS0828 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0828"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0828"
ms.assetid: e18ffe72-2fcc-436d-be7f-8c8365b86129
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0828 de erro do compilador
Não é possível atribuir 'expression' à propriedade de tipo anônimo.  
  
 Um tipo anônimo não pode ser inicializado com um valor nulo ou um tipo não seguro, ou um grupo de método ou função anônima.  
  
### Para corrigir este erro  
  
1.  Adicione uma declaração de tipo para o lado esquerdo da atribuição ou altere a expressão no lado direito para que ele tenha um tipo aceitável.  
  
## Exemplo  
 O código a seguir gera CS0828 porque um membro de um tipo anônimo não pode ser inicializado com um valor nulo.  
  
```  
// cs0828.cs using System; public class C { public static int Main() { var a = 1; var c = new { p1 = null }; // CS0828 return 1; } }  
```  
  
## Consulte também  
 [Variáveis locais de tipo implícito](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)