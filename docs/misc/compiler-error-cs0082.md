---
title: "CS0082 de erro do compilador | Microsoft Docs"
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
  - "CS0082"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0082"
ms.assetid: 7612976f-de2c-4f6b-87c9-43175821650c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0082 de erro do compilador
O tipo 'type' já reservou um membro chamado 'name' com os mesmos tipos de parâmetro  
  
 Propriedades em tempo de compilação são traduzidas para métodos com `get_` e\/ou `set_` na frente do identificador. Se você definir seu próprio método que está em conflito com o nome do método, um erro será gerado.  
  
## Exemplo  
 O exemplo a seguir gera CS0082:  
  
```  
//cs0082.cs class MyClass { //property public int MyProp { get //CS0082 { return 1; } } //conflicting Get public int get_MyProp() { return 2; } public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [Propriedades](/dotnet/csharp/programming-guide/classes-and-structs/properties)