---
title: "Compilador CS0280 de aviso (n&#237;vel 2) | Microsoft Docs"
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
  - "CS0280"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0280"
ms.assetid: 9b453478-92aa-4fd2-9b87-780fd138603a
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS0280 de aviso (n&#237;vel 2)
'type' não implementa o padrão de nome do padrão. nome do método tem a assinatura incorreta.  
  
 Duas instruções no c\#, **foreach** e **using**, dependem de padrões predefinidos, "coleção" e "recurso" respectivamente. Este aviso ocorre quando o compilador não pode corresponder a uma dessas instruções para seu padrão devido a assinatura incorreta do método. Por exemplo, o padrão "coleção" exige um método chamado <xref:System.Collections.IEnumerator.MoveNext%2A> que não usa nenhum parâmetro e retorna um `boolean`. Seu código pode conter um <xref:System.Collections.IEnumerator.MoveNext%2A> método que tem um parâmetro ou talvez retorna um objeto.  
  
 O padrão "recurso" e `using` fornecem outro exemplo. O padrão "recurso" requer o <xref:System.IDisposable.Dispose%2A> método; se você definir uma propriedade com o mesmo nome, você receberá esse aviso.  
  
 Para resolver este aviso, certifique\-se de que as assinaturas de método em seu tipo correspondem às assinaturas dos métodos correspondentes no padrão e certifique\-se de que você não têm nenhuma propriedade com o mesmo nome que um método exigido pelo padrão.  
  
## Exemplo  
 O exemplo a seguir gera CS0280.  
  
```  
// CS0280.cs using System; using System.Collections; public class ValidBase: IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } } class Derived : ValidBase { // field, not method new public int GetEnumerator; } public class Test { public static void Main() { foreach (int i in new Derived()) {}   // CS0280 } }  
```