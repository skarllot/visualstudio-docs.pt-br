---
title: "Compilador CS0824 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS0824"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0824"
ms.assetid: ad643bb7-51b2-455b-a9f3-2bd4588d2c5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0824 de aviso (n&#237;vel 1)
Construtor 'name' está marcado como externo.  
  
 Um construtor pode ser marcado como externo. No entanto, o compilador não pode verificar se o construtor realmente existe. Portanto, o aviso será gerado.  
  
### Para remover esse aviso  
  
1.  Use uma diretiva de aviso pragma para ignorá\-lo.  
  
2.  Mova o construtor dentro do tipo.  
  
## Exemplo  
 O código a seguir gera CS0824:  
  
```  
// cs0824.cs public class C { extern C(); // CS0824 public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [extern](/dotnet/csharp/language-reference/keywords/extern)   
 [\#pragma warning](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning)