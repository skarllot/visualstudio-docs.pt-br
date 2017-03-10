---
title: "CS1661 de erro do compilador | Microsoft Docs"
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
  - "CS1661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1661"
ms.assetid: 162d5736-ca3c-4a09-a5d9-a19da3d5bf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1661 de erro do compilador
Não é possível converter o bloco de método anônimo delegate ' tipo delegado ' porque os tipos de parâmetro do bloco especificado não correspondem aos tipos de parâmetro delegate  
  
 Esse erro ocorre se, em uma definição de método anônimo, os tipos de parâmetro do método anônimo não correspondem aos tipos de parâmetro delegate. Verificar o número de parâmetros, os tipos de parâmetro e qualquer ref ou parâmetros de saída e uma correspondência exata.  
  
 O exemplo a seguir gera CS1661:  
  
```  
// CS1661.cs delegate void MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(string s) { };  // CS1661 } }  
```