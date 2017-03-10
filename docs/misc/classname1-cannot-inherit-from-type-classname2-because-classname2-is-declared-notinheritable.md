---
title: "&#39;&lt; classname1 &gt;&#39; n&#227;o pode herdar de &lt; tipo &gt; &#39;&lt; classname2 &gt;&#39; como &#39;&lt; classname2 &gt;&#39; &#233; declarado &#39;NotInheritable&#39; | Microsoft Docs"
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
  - "vbc30299"
  - "bc30299"
helpviewer_keywords: 
  - "BC30299"
ms.assetid: 627d50f5-9e75-495d-93f7-50096ba2ea08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; classname1 &gt;&#39; n&#227;o pode herdar de &lt; tipo &gt; &#39;&lt; classname2 &gt;&#39; como &#39;&lt; classname2 &gt;&#39; &#233; declarado &#39;NotInheritable&#39;
Uma classe tenta herdar de outra classe, mas a classe base desejada é especificada como `NotInheritable`.`NotInheritable` classes são usadas principalmente para impedir derivação não intencional.  
  
 **ID do erro:** BC30299  
  
### Para corrigir este erro  
  
-   Remover o `NotInheritable` palavra\-chave da definição da classe base desejada ou remova o `Inherits` instrução.  
  
## Consulte também  
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Instrução Inherits](/dotnet/visual-basic/language-reference/statements/inherits-statement)