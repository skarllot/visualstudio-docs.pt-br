---
title: "CS1643 de erro do compilador | Microsoft Docs"
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
  - "CS1643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1643"
ms.assetid: 521f352b-00fb-4d62-89be-44251db3cc5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1643 de erro do compilador
Nem todos os caminhos de código retornam um valor no método do tipo 'type'\!  
  
 Esse erro ocorre se um corpo do delegado não tem uma instrução de retorno, ou se tiver uma instrução return que o compilador é capaz de verificar seja atingida. O exemplo a seguir, o compilador tentará prever o resultado da condição de ramificação para verificar se o bloco de método anônimo sempre retorna um valor.  
  
## Exemplo  
 O exemplo a seguir gera CS1643:  
  
```  
// CS1643.cs delegate int MyDelegate(); class C { static void Main() { MyDelegate d = delegate {                 // CS1643 int i = 0; if (i == 0) return 1; }; } }  
```