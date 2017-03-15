---
title: "Compilador CS0657 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS0657"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0657"
ms.assetid: d12d2efc-f44e-40e6-b825-5a66ead0c08e
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0657 de aviso (n&#237;vel 1)
'modificador de atributo ' não é um local de atributo válido para esta declaração. Locais de atributo válidos para esta declaração são 'locais'. Todos os atributos neste bloco serão ignorados.  
  
 O compilador encontrar um modificador de atributo em um local inválido. Consulte [destinos de atributos](http://msdn.microsoft.com/pt-br/59a261f0-1cfb-4aa5-b610-6b735389882c) para obter mais informações.  
  
 O exemplo a seguir gera CS0657:  
  
```  
// CS0657.cs // compile with: /target:library public class TestAttribute : System.Attribute {} [return: Test]   // CS0657 return not valid on a class class Class1 {}  
```