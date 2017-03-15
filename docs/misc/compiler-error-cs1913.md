---
title: "CS1913 de erro do compilador | Microsoft Docs"
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
  - "CS1913"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1913"
ms.assetid: 652494b3-9576-4a4c-a9ee-695f86c4a023
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1913 de erro do compilador
Membro 'name' não pode ser inicializado. Não é um campo ou propriedade.  
  
 Inicializadores de objeto só podem ser usados para inicializar campos ou propriedades acessíveis.  
  
### Para corrigir este erro  
  
1.  Inicialize o membro da classe em um construtor regular ou outro método de inicialização.  
  
## Exemplo  
 O exemplo a seguir gera CS1913:  
  
```  
// cs1912.cs class A { public delegate void D(); public event D myEvent; } public class Test { static void Main() { A a = new A() {myEvent = M}; // CS1913 } public void M(){} }  
```  
  
## Consulte também  
 [Classes e structs](/dotnet/csharp/programming-guide/classes-and-structs/index)