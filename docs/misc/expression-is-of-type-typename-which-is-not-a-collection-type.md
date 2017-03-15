---
title: "Express&#227;o &#233; do tipo &#39;&lt; typename &gt;&#39;, que n&#227;o &#233; um tipo de cole&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32023"
  - "vbc32023"
helpviewer_keywords: 
  - "BC32023"
ms.assetid: d0f151be-6b65-498b-b571-03faf24df0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o &#233; do tipo &#39;&lt; typename &gt;&#39;, que n&#227;o &#233; um tipo de cole&#231;&#227;o
A variável de grupo especificada em um `For Each` instrução não é um objeto de coleção ou matriz, e seu tipo não implementa o <xref:System.Collections.IEnumerable> interface. O tipo deve o suporte a [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] padrão de design de coleção ou implementar <xref:System.Collections.IEnumerable>.  
  
 **ID do erro:** BC32023  
  
### Para corrigir este erro  
  
-   Declarar a variável de grupo para ser de um tipo de classe que o oferece suporte a [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] design de coleção ou implementa <xref:System.Collections.IEnumerable>.  
  
## Consulte também  
 <xref:System.Collections.IEnumerable>   
 [Instrução For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [Classe de coleção do Visual Basic](http://msdn.microsoft.com/pt-br/0cb2d1ad-c58d-42c0-8e69-d81f5a15e532)