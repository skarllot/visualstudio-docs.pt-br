---
title: "CS0250 de erro do compilador | Microsoft Docs"
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
  - "CS0250"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0250"
ms.assetid: a994f361-6287-4db0-9ce1-e293a8190049
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0250 de erro do compilador
Não chame diretamente o método Finalize de classe base. Ele é chamado automaticamente pelo seu destruidor.  
  
 Um programa não pode tentar forçar a limpeza de recursos de classe base.  
  
 Consulte [métodos Finalize e destruidores](http://msdn.microsoft.com/pt-br/fd376774-1643-499b-869e-9546a3aeea70) para obter mais informações.  
  
 O exemplo a seguir gera CS0250  
  
```  
// CS0250.cs class B { } class C : B { ~C() { base.Finalize();   // CS0250 } public static void Main() { } }  
```