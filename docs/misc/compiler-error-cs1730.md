---
title: "CS1730 de erro do compilador | Microsoft Docs"
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
  - "CS1730"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1730"
ms.assetid: 20900ca0-702f-4f35-9a60-2dee9cb11902
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1730 de erro do compilador
Atributos de assembly e module devem preceder todos os outros elementos definidos em um arquivo, exceto as cláusulas using e as declarações de alias extern.  
  
 Um atributo aplicado no nível do assembly não pode aparecer após quaisquer definições de tipo.  
  
### Para corrigir este erro  
  
1.  Mover o atributo à parte superior do arquivo, mas abaixo do `using` diretivas e `extern` as declarações de alias.  
  
## Exemplo  
 O código a seguir gera CS1730:  
  
```  
// cs1730.cs class Test { } [assembly: System.Attribute] // CS1730  
```  
  
## Consulte também  
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)