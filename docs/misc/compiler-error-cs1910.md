---
title: "CS1910 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1910"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1910"
ms.assetid: 0fef9727-e56f-451c-9255-ca4e5a26d7c6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1910 de erro do compilador
Argumento do tipo 'type' não é aplicável para o atributo DefaultValue  
  
 Para parâmetros cujo tipo de objeto, o argumento do <xref:System.Runtime.InteropServices.DefaultParameterValueAttribute> deve ser `null`, um tipo integral, ponto flutuante, `bool`, `string`, `enum`, ou `char`. O argumento não pode ser do tipo <xref:System.Type> ou qualquer tipo de matriz.  
  
## Exemplo  
 O exemplo a seguir gera CS1910.  
  
```  
// CS1910.cs // compile with: /target:library using System.Runtime.InteropServices; public interface MyI { void Test([DefaultParameterValue(typeof(object))] object o);   // CS1910 }  
```