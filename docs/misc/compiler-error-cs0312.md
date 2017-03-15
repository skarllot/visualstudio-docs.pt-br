---
title: "CS0312 de erro do compilador | Microsoft Docs"
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
  - "CS0312"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0312"
ms.assetid: 552db0ae-2ecf-4beb-9606-bbe58e5708f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0312 de erro do compilador
O tipo 'type1' não pode ser usado como tipo parâmetro 'name' no genérico tipo ou método 'nome'. O tipo anulável 'type1' não satisfaz a restrição de 'type2'.  
  
 Um tipo anulável é diferente de sua contraparte não\-nulo; Nenhum referência conversão ou identificar existe conversão entre eles. Uma conversão boxing anuláveis não satisfaz uma restrição de tipo genérico. No exemplo a seguir, o primeiro parâmetro de tipo é um `Nullable<int>` e o segundo parâmetro de tipo é um `System.Int32`.  
  
### Para corrigir este erro  
  
1.  Remova a restrição.  
  
2.  No exemplo a seguir, tornar o segundo argumento de tipo ou `int?` ou `object`.  
  
## Exemplo  
 O código a seguir gera CS0312:  
  
```  
// cs0312.cs class Program { static void MTyVar<T, U>() where T : U { } static int Main() { MTyVar<int?, int>(); // CS0312 return 1; } }  
```  
  
 Embora um tipo anulável é diferente de um tipo não anulável, vários tipos de conversões são permitidos entre valores nulos e não anuláveis.  
  
## Consulte também  
 [Tipos anuláveis](/dotnet/csharp/programming-guide/nullable-types/index)