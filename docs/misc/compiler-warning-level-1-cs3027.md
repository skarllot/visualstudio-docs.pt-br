---
title: "Compilador CS3027 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3027"
ms.assetid: c515e623-3f5a-49fa-a878-f1d8e90fdc24
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3027 de aviso (n&#237;vel 1)
'type\_1' não é compatível com CLS porque a interface base 'type\_2' não é compatível com CLS  
  
 Um tipo compatível com CLS não não pode ser um tipo base para um tipo que é compatível com CLS.  
  
## Exemplo  
 O exemplo a seguir contém uma interface com um método que usa um tipo compatível com CLS não em sua assinatura, tornando o tipo não\-CLS compatível.  
  
```  
// CS3027.cs // compile with: /target:library public interface IBase { void IMethod(uint i); }  
```  
  
## Exemplo  
 O exemplo a seguir gera CS3027.  
  
```  
// CS3027_b.cs // compile with: /reference:CS3027.dll /target:library /W:1 [assembly:System.CLSCompliant(true)] public interface IDerived : IBase {}  
```