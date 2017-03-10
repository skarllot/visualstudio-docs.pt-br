---
title: "CS0820 de erro do compilador | Microsoft Docs"
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
  - "CS0820"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0820"
ms.assetid: 38c05162-ef20-42a8-9611-02698360dec5
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0820 de erro do compilador
Não é possível atribuir o inicializador de matriz para um local digitada implicitamente  
  
 Uma matriz digitada implicitamente é uma matriz cujo tipo de elemento é inferido pelo compilador. Ele deve ser inicializado usando o `new`\[\] modificador conforme mostrado no exemplo de código.  
  
### Para corrigir este erro  
  
-   Use o `new`\[\] modificador com o inicializador de matriz.  
  
-   Não use uma variável local digitada implicitamente.  
  
## Exemplo  
 O código a seguir gera CS0820 e mostra como inicializar uma matriz digitada implicitamente corretamente:  
  
```  
//cs0820.cs class G { public static int Main() { var a = { 1,2,3}; //CS0820 // Try using one of the following lines instead. // var b = new[] { 1, 2, 3 }; //int[] b = {1, 2, 3}; return -1; } }  
```  
  
## Consulte também  
 [Variáveis locais de tipo implícito](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)