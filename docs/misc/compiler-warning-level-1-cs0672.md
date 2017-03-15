---
title: "Compilador CS0672 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS0672"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0672"
ms.assetid: 140a8708-97d0-444b-980b-62e74328cafb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0672 de aviso (n&#237;vel 1)
Membro 'member1' substitui o membro obsoleto ' membro2. Adicionar o obsoleto atributo 'member1'  
  
 O compilador encontrou um `override` para um método marcado como `obsolete`. No entanto, o método de substituição não foi marcado como obsoleto. Substituindo o método ainda irá gerar [CS0612](/dotnet/csharp/misc/cs0612), se a chamada.  
  
 Revise suas declarações de método e indicar explicitamente se um método \(e todos os seus substituições\) devem ser marcados `obsolete`.  
  
 O exemplo a seguir gera CS0672:  
  
```  
// CS0672.cs // compile with: /W:1 class MyClass { [System.Obsolete] public virtual void ObsoleteMethod() { } } class MyClass2 : MyClass { public override void ObsoleteMethod()   // CS0672 { } } class MainClass { static public void Main() { } }  
```