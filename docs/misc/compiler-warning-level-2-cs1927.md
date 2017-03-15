---
title: "Compilador CS1927 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS1927"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1927"
ms.assetid: 32b4e58f-668c-4596-9529-7f3a293ff4ac
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1927 de aviso (n&#237;vel 2)
Ignorando \/win32manifest do módulo porque ele só se aplica aos assemblies.  
  
 Um manifesto win32 só é aplicado no nível do assembly. O módulo será compilado, mas não terá um manifesto.  
  
### Para corrigir este erro  
  
1.  Remover o **\/win32manifest option**.  
  
2.  Compile o código como um assembly.  
  
## Exemplo  
 O exemplo a seguir gera CS1927 quando compilado com ambos os **\/target:module** e **\/win32manifest** Opções do compilador.  
  
```  
// cs1927.cs // Compile with: /target:module /win32manifest using System; class ManifestWithModule { static int Main() { return 1; } }  
```  
  
## Consulte também  
 [\/win32manifest \(Import a Custom Win32 Manifest File\)](/dotnet/csharp/language-reference/compiler-options/win32manifest-compiler-option)   
 [\/target:module \(Create Module to Add to Assembly\)](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md)