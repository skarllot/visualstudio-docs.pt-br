---
title: "CS0825 de erro do compilador | Microsoft Docs"
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
  - "CS0825"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0825"
ms.assetid: 49393d23-ec5f-4b44-a3fd-7e0a95ac0edd
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0825 de erro do compilador
A palavra\-chave contextual 'var' só pode aparecer dentro de uma declaração de variável local.  
  
 Digitação implícita com o `var` palavra\-chave só pode ser aplicado às variáveis no escopo do método local.  
  
### Para corrigir este erro  
  
1.  Se a variável pertence no escopo da classe, dê a ele um tipo explícito.  Caso contrário, mova\-o dentro do método onde ele será usado.  
  
## Exemplo  
 O código a seguir gera CS0825 porque `var` é usado em um campo de classe:  
  
```  
// cs0825.cs class Test { private var myField; //CS0825 static int Main() { var a = 1; // var is OK here return -1; } }  
```  
  
## Consulte também  
 [Variáveis locais de tipo implícito](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)