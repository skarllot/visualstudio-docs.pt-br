---
title: "A palavra-chave &#39;&lt; palavra-chave &gt;&#39; &#233; usada para sobrecarregar membros herdados; N&#227;o use a palavra-chave &#39;&lt; palavra-chave &gt;&#39; quando sobrecarregando &#39;Sub New&#39; | Microsoft Docs"
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
  - "vbc32040"
  - "bc32040"
helpviewer_keywords: 
  - "BC32040"
ms.assetid: 39e6ee0d-b8a0-498e-bdaf-a4ceb13892fe
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A palavra-chave &#39;&lt; palavra-chave &gt;&#39; &#233; usada para sobrecarregar membros herdados; N&#227;o use a palavra-chave &#39;&lt; palavra-chave &gt;&#39; quando sobrecarregando &#39;Sub New&#39;
Um construtor está declarado com a `Overloads` palavra\-chave.  
  
 Visual Basic não dá suporte a herança ou de sobrecarga construtores.  
  
 **ID do erro:** BC32040  
  
### Para corrigir este erro  
  
-   Remover o `Overloads` palavra\-chave de todas as declarações de construtor.  
  
## Consulte também  
 [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)