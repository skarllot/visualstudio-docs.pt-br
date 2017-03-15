---
title: "CS0316 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0316"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0316"
ms.assetid: 8b70abbe-dd4f-473f-8dfe-f8309abef276
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0316 de erro do compilador
O parâmetro nome 'name' está em conflito com um nome de parâmetro gerado automaticamente.  
  
 Palavras reservadas não podem ser usadas como nomes de parâmetro. No exemplo a seguir, `value` é uma palavra reservada no contexto de um acessador de propriedade ou indexador padrão.  
  
### Para corrigir este erro  
  
1.  Altere o nome do parâmetro.  
  
## Exemplo  
 O código a seguir gera CS0316:  
  
```  
// cs0316.cs // Compile with: /target:library public class Test { public int this[int value] // CS0316 { get { return 1; } set { } } }  
```  
  
## Consulte também  
 [Indexadores](/dotnet/csharp/programming-guide/indexers/index)   
 [Palavras\-chave C\#](/dotnet/csharp/language-reference/keywords/index)