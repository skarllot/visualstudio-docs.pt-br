---
title: "Caractere de tipo n&#227;o pode ser usado em uma declara&#231;&#227;o &#39;Sub&#39; porque &#39;Sub&#39; n&#227;o retorna um valor | Microsoft Docs"
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
  - "bc30303"
  - "vbc30303"
helpviewer_keywords: 
  - "BC30303"
ms.assetid: f5a744f0-d312-4fe3-90cd-3cf372a93664
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Caractere de tipo n&#227;o pode ser usado em uma declara&#231;&#227;o &#39;Sub&#39; porque &#39;Sub&#39; n&#227;o retorna um valor
Um `Sub` procedimento, como uma `Function` procedimento, é um procedimento separado que pode usar argumentos e executar uma série de instruções. Ao contrário de uma `Function` procedimento, um `Sub` não retorna um valor e, portanto, não pode conter uma declaração de tipo.  
  
 **ID do erro:** BC30303  
  
### Para corrigir este erro  
  
-   Alterar o `Sub` procedimento para uma `Function` procedimento.  
  
## Consulte também  
 [Subprocedimentos](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)   
 [Procedimentos de função](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)