---
title: "Compilador CS3023 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3023"
ms.assetid: fd7782f9-f18a-4ce8-843b-95bf19b54317
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3023 de aviso (n&#237;vel 1)
O atributo CLSCompliant não tem sentido quando aplicado a tipos de retorno.  Tente colocá\-lo no método.  
  
 Tipos não são verificados para compatibilidade com CLS, desde que as regras de compatibilidade com CLS se aplicam a métodos e declarações de tipo de retorno da função.  
  
## Exemplo  
 O exemplo a seguir gera um aviso CS3023:  
  
```  
// C3023.cs [assembly:System.CLSCompliant(true)] public class Test { [return:System.CLSCompliant(true)]  // CS3023 // Try this instead: // [method:System.CLSCompliant(true)] public static int Main() { return 0; } }  
```