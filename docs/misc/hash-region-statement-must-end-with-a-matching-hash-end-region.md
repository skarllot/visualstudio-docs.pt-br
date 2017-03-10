---
title: "&#39;#Region&#39; deve finalizar com &#39;#End Region&#39; correspondente | Microsoft Docs"
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
  - "bc30681"
  - "vbc30681"
helpviewer_keywords: 
  - "BC30681"
ms.assetid: 05a0402b-da68-4ab8-b6d6-940379bc5973
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#Region&#39; deve finalizar com &#39;#End Region&#39; correspondente
Use o `#Region` diretiva para especificar um bloco de código que você pode expandir ou recolher ao usar o recurso de estruturação do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor de códigos. O início e fim de `#Region` instruções devem estar no mesmo bloco de código.  
  
 **ID do erro:** BC30681  
  
### Para corrigir este erro  
  
1.  Inserir `#End Region` no local apropriado do código após o `#Region` instrução.  
  
## Consulte também  
 [Diretiva \#Region](/dotnet/visual-basic/language-reference/directives/region-directive)