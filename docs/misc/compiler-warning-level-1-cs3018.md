---
title: "Compilador CS3018 de aviso (n&#237;vel 1) | Microsoft Docs"
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
  - "CS3018"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3018"
ms.assetid: 35d2f4bd-10c3-4e9f-8e02-389ab84db2cd
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilador CS3018 de aviso (n&#237;vel 1)
'type' não pode ser marcado como compatível com CLS porque ele é um membro do tipo não compatível com CLS 'type'  
  
 Este aviso ocorre se uma classe aninhada com o atributo CLSCompliant para `true` é declarado como um membro de uma classe é declarada com o atributo CLSCompliant para `false`. Isso não é permitido, como uma classe aninhada não pode ser compatível com CLS se ele for um membro de uma classe externa que não é compatível com CLS. Para resolver esse aviso, remova o atributo CLSCompliant da classe aninhada ou alterá\-lo de `true` para `false`. Para obter mais informações sobre compatibilidade com CLS, consulte [Escrevendo código compatível com CLS](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3) e [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemplo  
 O exemplo a seguir gera CS3018.  
  
```  
// CS3018.cs // compile with: /target:library using System; [assembly: CLSCompliant(true)] [CLSCompliant(false)] public class Outer { [CLSCompliant(true)]   // CS3018 public class Nested {} // OK public class Nested2 {} [CLSCompliant(false)] public class Nested3 {} }  
```