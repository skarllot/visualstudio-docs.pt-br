---
title: "Resolu&#231;&#227;o sobrecarregada falhou porque nenhum &#39;&lt; m&#233;todo acess&#237;vel &gt;&#39; pode ser chamado sem uma convers&#227;o de restri&#231;&#227;o: &lt; erro &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30519"
  - "bc30519"
helpviewer_keywords: 
  - "BC30519"
ms.assetid: 3b3e724d-6fad-4146-b47d-6525493b2fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Resolu&#231;&#227;o sobrecarregada falhou porque nenhum &#39;&lt; m&#233;todo acess&#237;vel &gt;&#39; pode ser chamado sem uma convers&#227;o de restri&#231;&#227;o: &lt; erro &gt;
Você fez uma chamada para um método sobrecarregado, mas o compilador não pode localizar um método que pode ser chamado sem uma conversão de restrição. Uma conversão de restrição muda o valor para um tipo de dados que pode não ser capaz de manter precisamente algum dos possíveis valores.  
  
 **ID do erro:** BC30519  
  
### Para corrigir este erro  
  
-   Especifique `Option Strict Off`.  
  
## Consulte também  
 [Propriedades e métodos sobrecarregados](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Conversões de Widening e Narrowing](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Instrução Option Strict](/dotnet/visual-basic/language-reference/statements/option-strict-statement)