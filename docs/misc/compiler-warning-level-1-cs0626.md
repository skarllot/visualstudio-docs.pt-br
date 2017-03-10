---
title: "Compilador CS0626 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS0626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0626"
ms.assetid: 2cd5061c-80e7-48d3-8d14-be7fc642af94
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0626 de aviso (n&#237;vel 1)
Método, operador ou o acessador 'method' está marcado como externo e sem atributos. Considere a adição de um atributo DllImport para especificar a implementação externa  
  
 Um método marcado `extern` também deve ser marcado com um atributo, por exemplo, o [DllImport](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic) atributo.  
  
 O atributo especifica onde o método é implementado. Em tempo de execução, essas informações serão necessárias para o programa.  
  
 O exemplo a seguir gera CS0626:  
  
```  
// CS0626.cs // compile with: /warnaserror using System.Runtime.InteropServices; public class MyClass { static extern public void M(); // CS0626 // try the following line // [DllImport("mydll.dll")] static extern public void M(); public static void Main() { } }  
```