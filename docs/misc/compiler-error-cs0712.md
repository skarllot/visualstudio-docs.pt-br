---
title: "CS0712 de erro do compilador | Microsoft Docs"
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
  - "CS0712"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0712"
ms.assetid: cde64c0c-3953-4563-8c24-8b646230bbb8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0712 de erro do compilador
Não é possível criar uma instância da classe static 'classe estática'  
  
 Não é possível criar instâncias de classes estáticas. Classes estáticas são projetadas para conter campos e métodos estáticos, mas não podem ser instanciadas.  
  
## Exemplo  
 O exemplo a seguir gera CS0712:  
  
```  
// CS0712.cs public static class SC { } public class CMain { public static void Main() { SC sc = new SC();  // CS0712 } }  
```