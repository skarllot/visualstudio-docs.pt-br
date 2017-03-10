---
title: "CS5001 de erro do compilador | Microsoft Docs"
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
  - "CS5001"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS5001"
ms.assetid: e1e26e75-84e0-47c7-be8a-3c4fd0d6f497
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS5001 de erro do compilador
Programa de' ' não contém um método 'Main' static adequado para um ponto de entrada  
  
 Esse erro ocorre quando não há estática [principal](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments) método com uma assinatura correta é encontrado no código que produz um arquivo executável. Esse erro também ocorrerá se a entrada de ponto de função, `Main`, é definido como no caso de errado, minúscula `main`.  
  
-   `Main` deve ser declarado como estático e deve retornar [void](/dotnet/csharp/language-reference/keywords/void) ou [int](/dotnet/csharp/language-reference/keywords/int), e deve ter um sem parâmetros ou então um parâmetro do tipo `string[]`.  
  
## Exemplo  
 O exemplo a seguir gera CS5001:  
  
```  
// CS5001.cs // CS5001 expected public class a { // Uncomment the following line to resolve. // static void Main() {} }  
```  
  
## Consulte também  
 [Main\(\) e argumentos de linha de comando](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments)