---
title: "&#39;#End Region&#39; deve ser precedido por um &#39;#Region&#39; correspondente | Microsoft Docs"
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
  - "vbc30680"
  - "bc30680"
helpviewer_keywords: 
  - "BC30680"
ms.assetid: 1ea60620-c8dc-4957-8cf4-07b25d20da3b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;#End Region&#39; deve ser precedido por um &#39;#Region&#39; correspondente
Com `#Region` você pode especificar um bloco de código para expandir ou recolher ao usar o recurso de estruturação do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor de códigos. O início e fim de `#Region` instruções devem estar no mesmo bloco de código.  
  
 **ID do erro:** BC30680  
  
### Para corrigir este erro  
  
-   Inserir `#Region` no local apropriado antes correspondente `#End` `Region` instrução.  
  
## Consulte também  
 [Diretiva \#Region](/dotnet/visual-basic/language-reference/directives/region-directive)