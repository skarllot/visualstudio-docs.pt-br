---
title: "Compilador CS1718 de aviso (n&#237;vel 3) | Microsoft Docs"
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
  - "CS1718"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1718"
ms.assetid: 7c1c11fd-4f91-482d-b8f7-efe2a361634e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1718 de aviso (n&#237;vel 3)
Comparação feita à mesma variável. Você pretendia comparar com outro elemento?  
  
 Se você pretendia comparar com algo, em seguida, você deve corrigir a instrução.  
  
 Mas outra possibilidade é que você estivesse testando para true ou false e estava fazendo isso pelas instruções como `if (a == a) (true)` ou `if (a < a) (false)`. É melhor simplesmente dizer `if (true)` ou `if (false)`. Há dois motivos para isso:  
  
-   É mais simples: é sempre mais clara simplesmente dizer o que significa.  
  
-   Ele ajuda a evitar confusão: tipos de valor anulável, que são análogos para o valor de é um novo recurso do c\# 2.0 `null` em T\-SQL, a linguagem de programação usada pelo SQL Server. Os desenvolvedores familiarizados com o T\-SQL podem se preocupar com o efeito de tipos anuláveis em expressões, como `if (a == a)`, devido ao uso de lógica Ternário em T\-SQL. Se você usar `true` ou `false`, evitar essa confusão possíveis.  
  
## Exemplo  
 O código a seguir gera um aviso CS1718.  
  
```  
// CS1718.cs using System; public class Tester { public static void Main() { int i = 0; if (i == i) { // CS1718.cs //if (true) { i++; } } }  
```