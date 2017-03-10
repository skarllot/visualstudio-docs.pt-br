---
title: "Compilador CS0114 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0114"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0114"
ms.assetid: 9647772b-d581-4620-981e-f9c607d4a1af
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0114 de aviso (n&#237;vel 2)
'function1' oculta o membro herdado 'function2'. Para fazer com que o método atual substitua esta implementação, adicione a palavra\-chave override. Caso contrário, adicione a nova palavra\-chave.  
  
 Uma declaração de uma classe está em conflito com uma declaração de uma classe base que o membro da classe base será oculto.  
  
 Para obter mais informações, consulte [base](/dotnet/csharp/language-reference/keywords/base).  
  
 O exemplo a seguir gera CS0114:  
  
```  
// CS0114.cs // compile with: /W:2 /warnaserror abstract public class clx { public abstract void f(); } public class cly : clx { public void f() // CS0114, hides base class member // try the following line instead // override public void f() { } public static void Main() { } }  
```