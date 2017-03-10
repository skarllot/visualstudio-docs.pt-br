---
title: "CS2036 de erro do compilador | Microsoft Docs"
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
  - "CS2036"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2036"
ms.assetid: 44b73be4-b792-4735-bdbd-bd757ab22683
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS2036 de erro do compilador
A opção \/pdb requer que a opção \/debug também seja usada.  
  
 Arquivos de banco de dados do programa são gerados apenas para compilações de depuração. O **\/pdb** opção, portanto, faz sentida em uma versão comercial.  
  
### Para corrigir este erro  
  
-   Adicionar o **\/debug** opção de compilador.  
  
-   Remover o **\/pdb** opção de compilador.  
  
## Exemplo  
 O exemplo a seguir gera CS2036 quando compilado com o **\/pdb** opção, mas não a opção \/debug:  
  
```  
// cs2036.cs // Compile with: /pdb // CS2036 class Test { public static int Main() { return 1; } }  
```  
  
## Consulte também  
 [\/pdb \(Specify Debug Symbol File\)](/dotnet/csharp/language-reference/compiler-options/pdb-compiler-option)   
 [\/debug \(Emit Debugging Information\)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option)