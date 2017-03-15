---
title: "CS0118 de erro do compilador | Microsoft Docs"
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
  - "CS0118"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0118"
ms.assetid: 9a612432-6e56-4e9b-9d8c-7d7b43f58c1a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0118 de erro do compilador
'construct1\_name' é 'construct1', mas é usado como um 'construct2'  
  
 O compilador detectou uma situação em que foi usada uma construção de alguma forma, errada ou foi tentada uma operação não permitida em uma construção. Alguns exemplos comuns incluem o seguinte:  
  
-   Uma tentativa de instanciar um namespace \(em vez de uma classe\)  
  
-   Tentar chamar um campo \(em vez de um método\)  
  
-   Tentar usar um tipo como uma variável  
  
-   Uma tentativa de usar um alias extern como um tipo.  
  
 Para resolver esse erro, certifique\-se de que a operação que você está executando é válida para o tipo que você estiver executando a operação em.  
  
## Exemplo  
 O exemplo a seguir gera CS0118.  
  
```  
// CS0118.cs // compile with: /target:library namespace MyNamespace { class MyClass { // MyNamespace not a class MyNamespace ix = new MyNamespace ();   // CS0118 } }  
```