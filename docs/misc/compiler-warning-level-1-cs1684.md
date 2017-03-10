---
title: "Compilador CS1684 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS1684"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1684"
ms.assetid: 620419bf-b6d5-4cda-a549-fcacf2f08920
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS1684 de aviso (n&#237;vel 1)
Referência ao tipo 'Type Name' alega está definido em 'Namespace', mas não pôde ser encontrado  
  
 Esse erro pode ser causado por uma referência dentro de um namespace referindo\-se a um tipo que ele diz que existe dentro de um namespace de segundo, mas o tipo não existe. Por exemplo, mydll.dll diz desse tipo `A` existe em yourdll.dll, mas esse tipo não existe em yourdll.dll. Uma possível causa desse erro é que a versão do yourdll.dll que você está usando é muito antiga e `A` ainda não foi definido.  
  
 O exemplo a seguir gera CS1684.  
  
## Exemplo  
  
```  
// CS1684_a.cs // compile with: /target:library /keyfile:CS1684.key public class A { public void Test() {} } public class C2 {}  
```  
  
## Exemplo  
  
```  
// CS1684_b.cs // compile with: /target:library /r:cs1684_a.dll // post-build command: del /f CS1684_a.dll using System; public class Ref { public static A GetA() { return new A(); } public static C2 GetC() { return new C2(); } }  
```  
  
## Exemplo  
 Vamos agora, recompile o primeiro conjunto, omitindo a definição de classe C2 não a serem definidos na recompilação.  
  
```  
// CS1684_c.cs // compile with: /target:library /keyfile:CS1684.key /out:CS1684_a.dll public class A { public void Test() {} }  
```  
  
## Exemplo  
 Este módulo menciona o segundo módulo por meio do identificador `Ref`. Mas o segundo módulo contém uma referência à classe `C2`, que não existe mais devido a compilação na etapa anterior e, portanto, a mensagem de erro CS1684 é retornada da compilação deste módulo.  
  
```  
// CS1684_d.cs // compile with: /reference:cs1684_a.dll /reference:cs1684_b.dll // CS1684 expected class Tester { public static void Main() { Ref.GetA().Test(); } }  
```