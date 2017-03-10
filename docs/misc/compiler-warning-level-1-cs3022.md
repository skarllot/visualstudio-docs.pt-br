---
title: "Compilador CS3022 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3022"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3022"
ms.assetid: 9340645c-10c3-4e21-a825-3f05fae02ff7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3022 de aviso (n&#237;vel 1)
O atributo CLSCompliant não tem sentido quando aplicado aos parâmetros. Tente colocá\-lo no método.  
  
 Parâmetros de método não são verificados para compatibilidade com CLS, desde que as regras de compatibilidade com CLS se aplicam a métodos e declarações de tipo.  
  
## Exemplo  
 O exemplo a seguir gera CS3022:  
  
```  
// CS3022.cs // compile with: /W:1 using System; [assembly: CLSCompliant(true)] [CLSCompliant(true)] public class C { public void F([CLSCompliant(true)] int i) { } public static void Main() { } }  
```