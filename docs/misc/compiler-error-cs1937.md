---
title: "CS1937 de erro do compilador | Microsoft Docs"
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
  - "CS1937"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1937"
ms.assetid: f13e8dc9-8c20-477e-8b74-7192848e08a2
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1937 de erro do compilador
O nome 'name' não está no escopo à esquerda de 'equals'. Considere trocar as expressões em ambos os lados de 'equals'.  
  
 O `equals` palavra\-chave é um operador especial que é usado em um `join` cláusula para determinar igualdade entre duas expressões. A variável de intervalo para a sequência de origem do lado esquerdo está no escopo à esquerda de equals e a variável de intervalo para a fonte do lado direito é somente no escopo no lado esquerdo de equals. Você pode verificar isso experimentando o IntelliSense no exemplo de código a seguir.  
  
### Para corrigir este erro  
  
1.  Troca a posição das variáveis de intervalo de dois, como mostra a linha comentada no exemplo a seguir:  
  
## Exemplo  
 O exemplo a seguir gera CS1937.  
  
```  
// cs1937.cs using System.Linq; class Test { static void Main() { int[] sourceA = { 1, 2, 3, 4, 5 }; int[] sourceB = { 3, 4, 5, 6, 7 }; var query = from a in sourceA join b in sourceB on b equals a // CS1937 // Try the following line instead. //join b in sourceB on a equals b select new { a, b }; } }  
```  
  
 O lado esquerdo é geralmente chamado lado "externo" e à direita é geralmente chamada lado "interno".  
  
## Consulte também  
 [Cláusula join](/dotnet/csharp/language-reference/keywords/join-clause)