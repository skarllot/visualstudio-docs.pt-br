---
title: "CS0227 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0227"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0227"
ms.assetid: b595a1c9-8204-4ff7-a1d0-258b0b1d6ff7
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS0227 de erro do compilador
Código sem segurança só pode aparecer se a compilação for com \/unsafe  
  
 Se o código\-fonte contém o [unsafe](/dotnet/csharp/language-reference/keywords/unsafe) palavra\-chave, o [\/unsafe](/dotnet/csharp/language-reference/compiler-options/unsafe-compiler-option) também deve ser usada a opção de compilador. Para obter mais informações, consulte [Código não seguro e ponteiros](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 Para definir a opção \/unsafe em [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], clique em **projeto** no menu principal, selecione o **criar** painel e marque a caixa que diz "permitir que código não seguro".  
  
 O exemplo a seguir, quando compilado sem **\/unsafe**, irá gerar CS0227:  
  
```  
// CS0227.cs public class MyClass { unsafe public static void Main()   // CS0227 { } }  
```  
  
## Consulte também  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)