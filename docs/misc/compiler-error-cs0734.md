---
title: "CS0734 de erro do compilador | Microsoft Docs"
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
  - "CS0734"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0734"
ms.assetid: 9e1b0e49-bfc3-400c-9fd1-37e3c827e656
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0734 de erro do compilador
A opção \/moduleassemblyname só pode ser especificada ao criar um tipo de destino de 'module'  
  
 A opção de compilador **\/moduleassemblyname** só deve ser usado ao criar um. netmodule. Consulte [\/moduleassemblyname \(Specify Friend Assembly for Module\)](/dotnet/csharp/language-reference/compiler-options/moduleassemblyname-compiler-option) para obter mais informações.  
  
 Para obter mais informações sobre a criação de um. netmodule, consulte [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md).  
  
## Exemplo  
 O exemplo a seguir gera CS0734. Para resolver, adicione **\/target:module** à compilação.  
  
```  
// CS0734.cs // compile with: /moduleassemblyname:A // CS0734 expected public class Test {}  
```