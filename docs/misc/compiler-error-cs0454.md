---
title: "CS0454 de erro do compilador | Microsoft Docs"
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
  - "CS0454"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0454"
ms.assetid: 2c83bc5e-53bb-473e-92aa-5122dadd79d1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0454 de erro do compilador
Dependência de restrição circular envolvendo '1 de parâmetro de tipo' e 'Tipo de parâmetro 2'  
  
 Este erro ocorre porque em algum momento refere\-se de um parâmetro de tipo para outro, e o segundo se refere ao primeiro. Para corrigir esse erro, quebre a dependência circular removendo uma das restrições. Observe que a dependência circular de restrição pode ser indireta.  
  
## Exemplo  
 O código a seguir gera erro CS0454.  
  
```  
// CS0554 using System; public class GenericsErrors { public class G4<T> where T : T { } // CS0454 }  
```  
  
## Exemplo  
 O exemplo a seguir demonstra uma dependência circular entre duas restrições de tipo.  
  
```  
public class Gen<T,U> where T : U where U : T  // CS0454 { }  
```