---
title: "CS1958 de erro do compilador | Microsoft Docs"
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
  - "CS1958"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1958"
ms.assetid: bb6f3bb2-ea93-4d2e-984c-da9c99f5653f
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1958 de erro do compilador
Expressões de inicializador de objeto e coleção não podem ser aplicadas a uma expressão de criação de delegado  
  
 Um delegado não tem membros que tem uma classe ou estrutura e, portanto, não há nada para um inicializador de objeto inicializar. Se você encontrar esse erro, provavelmente é porque há chaves após a expressão de criação de delegado. Remover apenas as chaves e esse erro desaparecerá.  
  
### Para corrigir este erro  
  
1.  Remova as chaves.  
  
## Exemplo  
 O código a seguir produz CS1958:  
  
```  
// cs1958.cs public class MemberInitializerTest { delegate void D<T>(); public static void GenericMethod<T>() { } public static void Run() { D<int> genD = new D<int>(GenericMethod<int>) { }; // CS1958 // Try the following line instead // D<int> genD = new D<int>(GenericMethod<int>); } }  
```