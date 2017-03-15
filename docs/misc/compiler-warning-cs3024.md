---
title: "CS3024 de aviso do compilador | Microsoft Docs"
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
  - "CS3024"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3024"
ms.assetid: fef9db31-9a7f-42d5-ad37-3e7faf661f95
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS3024 de aviso do compilador
Tipo de restrição 'type' não é compatível com CLS.  
  
 O compilador emite esse aviso porque o uso de um tipo não compatível com CLS como uma restrição de tipo genérico pode tornar impossível para código escrito em alguns idiomas para consumir sua classe genérica.  
  
### Para eliminar esse aviso  
  
1.  Use um tipo compatível com CLS para a restrição de tipo.  
  
## Exemplo  
 O exemplo a seguir gera CS3024 em vários locais:  
  
```  
// cs3024.cs // Compile with: /target:library [assembly: System.CLSCompliant(true)] [type: System.CLSCompliant(false)] public class TestClass // CS3024 { public ushort us; } [type: System.CLSCompliant(false)] public interface ITest // CS3024 {} public interface I<T> where T : TestClass {} public class TestClass_2<T> where T : ITest {} public class TestClass_3<T> : I<T> where T : TestClass {} public class TestClass_4<T> : TestClass_2<T> where T : ITest {} public class Test { public static int Main() { return 0; } }  
```  
  
## Consulte também  
 [Restrições a parâmetros de tipo](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)