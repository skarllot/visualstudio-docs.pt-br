---
title: "CS1670 de erro do compilador | Microsoft Docs"
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
  - "CS1670"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1670"
ms.assetid: ee2507e5-b509-4af3-a15e-2c1f2da7159c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1670 de erro do compilador
params não é válido neste contexto  
  
 Um número de recursos do c\# são incompatível com listas de argumentos de variável e não permitem o `params```palavra\-chave, incluindo o seguinte:  
  
-   Listas de parâmetros de métodos anônimos  
  
-   Operadores sobrecarregados  
  
## Exemplo  
 O exemplo a seguir gera CS1670:  
  
```  
// CS1670.cs public class C { public bool operator +(params int[] paramsList)  // CS1670 { return false; } static void Main() { } }  
```