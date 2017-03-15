---
title: "Essa heran&#231;a causa depend&#234;ncias circulares entre &lt; type1 &gt; &#39;&lt; typename1 &gt;&#39; e sua &lt; type2 &gt; aninhada &#39;&lt; typename2 &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30907"
  - "bc30907"
helpviewer_keywords: 
  - "BC30907"
ms.assetid: 17d4f938-5895-4d33-943e-8abf0ceacdc9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Essa heran&#231;a causa depend&#234;ncias circulares entre &lt; type1 &gt; &#39;&lt; typename1 &gt;&#39; e sua &lt; type2 &gt; aninhada &#39;&lt; typename2 &gt;&#39;
Uma estrutura de herança resulta em dependência circular entre classes aninhadas, ou seja, duas classes herdando uma da outra.  
  
 O código a seguir pode gerar essa mensagem de erro.  
  
```  
Public Class c1 Inherits c3.c4 Public Class c2 End Class End Class Public Class c3 Inherits c1.c2 Public Class c4 End Class End Class  
```  
  
 No código anterior, classe `c1` herda da classe `c4`, mas `c4` está aninhado em `c3`, que herda do `c2`, aninhado em `c1`.  
  
 **ID do erro:** BC30907  
  
### Para corrigir este erro  
  
-   Altere a estrutura de herança para que não haja nenhuma dependência circular.  
  
## Consulte também  
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)