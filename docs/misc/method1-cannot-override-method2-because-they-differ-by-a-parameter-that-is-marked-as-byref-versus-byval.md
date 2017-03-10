---
title: "&#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque eles diferem por um par&#226;metro que est&#225; marcado como &#39;ByRef&#39; versus &#39;ByVal&#39; | Microsoft Docs"
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
  - "vbc30398"
  - "bc30398"
helpviewer_keywords: 
  - "BC30398"
ms.assetid: 78d62276-4ad9-4876-8c35-a30c9c195638
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque eles diferem por um par&#226;metro que est&#225; marcado como &#39;ByRef&#39; versus &#39;ByVal&#39;
Você tentou substituir um método com outro método que difere em um parâmetro marcado como `ByRef` em vez de `ByVal`. Membros substituídos devem ter os mesmos argumentos como os membros herdados da classe base.  
  
 **ID do erro:** BC30398  
  
### Para corrigir este erro  
  
-   Verifique se os parâmetros estão ambos `ByRef` ou `ByVal`.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Passando argumentos por valor e por referência](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)