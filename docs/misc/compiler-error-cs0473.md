---
title: "CS0473 de erro do compilador | Microsoft Docs"
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
  - "CS0473"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0473"
ms.assetid: 58eb141e-7da0-41c8-b868-7cd2a15f07f9
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0473 de erro do compilador
Implementação de interface explícita 'nome do método' corresponde a mais de um membro de interface. Membro de interface, na verdade, é escolhido é dependente de implementação. Considere o uso de uma implementação não explícita.  
  
 Em alguns casos, um método genérico pode adquirir a mesma assinatura de um método não genérico. O problema é que não há nenhuma maneira comuns language infrastructure \(CLI\) metadados sistema para inequivocamente estado qual método associa a qual slot. Cabe a CLI para fazer essa determinação.  
  
> [!NOTE]
>  Esse erro é gerado no Visual Studio 2008 em lugares em que não foi gerado no Visual Studio 2005.  
  
### Para corrigir este erro  
  
1.  Eliminar a implementação explícita e apenas a implementação implícita `public int TestMethod(int)` implementar ambos os métodos de interface.  
  
## Exemplo  
 O código a seguir gera CS0473:  
  
```  
// cs0473.cs public interface ITest<T> { int TestMethod(int i); int TestMethod(T i); } public class ImplementingClass : ITest<int> { int ITest<int>.TestMethod(int i) // CS0473 { return i + 1; } public int TestMethod(int i) { return i - 1; } } class T { static int Main() { ImplementingClass a = new ImplementingClass(); if (a.TestMethod(0) != -1) return -1; ITest<int> i_a = a; System.Console.WriteLine(i_a.TestMethod(0).ToString()); if (i_a.TestMethod(0) != 1) return -1; return 0; } }  
  
```  
  
## Consulte também  
 [Aventuras fabulosas da codificação](http://blogs.msdn.com/ericlippert/archive/2006/04/06/570126.aspx)