---
title: "CS0410 de erro do compilador | Microsoft Docs"
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
  - "CS0410"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0410"
ms.assetid: a8b11042-9119-465e-abf6-235cbc7b8db5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0410 de erro do compilador
Nenhuma sobrecarga para 'method' tem o parâmetro correto e tipos de retorno  
  
 Esse erro ocorre se você tentar instanciar um delegado com uma função que tem os tipos de parâmetro incorreto. Os tipos de parâmetro do delegado devem corresponder a função que você está atribuindo o delegado.  
  
## Exemplo  
 O exemplo a seguir gera CS0410:  
  
```  
// CS0410.cs // compile with: /langversion:ISO-1 class Test { delegate void D(double d ); static void F(int i) { } static void Main() { D d = new D(F);  // CS0410 } }  
```