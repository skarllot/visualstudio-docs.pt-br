---
title: "CS1508 de erro do compilador | Microsoft Docs"
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
  - "CS1508"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1508"
ms.assetid: 979bc615-58ce-49f8-ba73-e6cf57c56418
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1508 de erro do compilador
Identificador de recurso 'identifier' já foi usado neste assembly  
  
 Em uma compilação, o mesmo identificador \(***identificador***\) foi passado para dois ou mais [\/resource](/dotnet/csharp/language-reference/compiler-options/resource-compiler-option) ou [\/linkresource](/dotnet/csharp/language-reference/compiler-options/linkresource-compiler-option) opções do compilador.  
  
 Por exemplo, as opções a seguir geraria CS1508:  
  
```  
/resource:anyfile.bmp,DuplicatIdent /linkresource:a.bmp,DuplicatIdent  
```