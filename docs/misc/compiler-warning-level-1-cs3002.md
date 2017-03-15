---
title: "Compilador CS3002 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3002"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3002"
ms.assetid: 34f19735-76d2-4d78-bd52-45989a86fca4
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3002 de aviso (n&#237;vel 1)
Tipo de retorno de 'method' não é compatível com CLS  
  
 Um [públicas](/dotnet/csharp/language-reference/keywords/public), [protegido](/dotnet/csharp/language-reference/keywords/protected), ou `protected` `internal` método deve retornar um valor cujo tipo é compatível com o Common Language Specification \(CLS\).  Para obter mais informações sobre compatibilidade com CLS, consulte [Escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3) e [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemplo  
 O exemplo a seguir gera CS3002:  
  
```  
// CS3002.cs [assembly:System.CLSCompliant(true)] public class a { public ushort bad()   // CS3002, public method { ushort a; a = ushort.MaxValue; return a; } private ushort OK()   // OK, private method { ushort a; a = ushort.MaxValue; return a; } public static void Main() { } }  
```