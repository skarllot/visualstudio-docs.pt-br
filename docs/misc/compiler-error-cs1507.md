---
title: "CS1507 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1507"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1507"
ms.assetid: e1be3aba-81dc-4f65-87a4-d3f90b82dc7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1507 de erro do compilador
Não é possível vincular o arquivo de recurso 'arquivo' ao criar um módulo  
  
 [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) foi usado na mesma compilação com [\/target: Module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md), que não é permitido. Por exemplo, as opções a seguir geraria CS1507:  
  
```  
csc /linkresource:rf.resource /target:module in.cs  
```  
  
 Embeding resourrces \([\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option)\), no entanto, é permitido.