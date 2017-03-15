---
title: "CS1944 de erro do compilador | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1944"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1944"
ms.assetid: e5e2c018-9a7e-48ee-8dd3-98e3553777c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# CS1944 de erro do compilador
Uma árvore de expressão não pode conter uma operação de ponteiro inseguro  
  
 Árvores de expressão não oferecem suporte a tipos de ponteiro porque o <xref:System.Linq.Expressions.Expression%601.Compile%2A?displayProperty=fullName> método só é permitido para produzir código verificável. Consulte comentários.  
  
### Para corrigir este erro  
  
1.  Não use tipos de ponteiro quando você está tentando criar uma árvore de expressão.  
  
## Exemplo  
 O exemplo a seguir gera CS1944:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Em algumas situações, é bom ter ponteiros em árvores de expressão. Por exemplo, considere o seguinte código:  
  
 `Expression<Func\<int*[], int*[]>) e = (int*[] i)=>i;`  
  
 Esse código é uma árvore de expressão porque nenhum argumento de tipo é tipos de ponteiro. Eles são matrizes de ponteiros e matrizes não são tipos de ponteiro. Além disso, o corpo da árvore de expressão não faz nada perigoso com qualquer ponteiro.  
  
## Consulte também  
 [unsafe](/dotnet/csharp/language-reference/keywords/unsafe)