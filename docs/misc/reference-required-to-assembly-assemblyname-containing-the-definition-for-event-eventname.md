---
title: "Refer&#234;ncia necess&#225;ria para o assembly &#39;&lt; assemblyname &gt;&#39; contendo a defini&#231;&#227;o para evento &#39;&lt; eventname &gt;&#39; | Microsoft Docs"
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
  - "vbc30005"
  - "bc30005"
helpviewer_keywords: 
  - "BC30005"
ms.assetid: 843b0b2f-0f93-41c3-8727-13a2138e8140
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia necess&#225;ria para o assembly &#39;&lt; assemblyname &gt;&#39; contendo a defini&#231;&#227;o para evento &#39;&lt; eventname &gt;&#39;
Referência necessária para o assembly ' \<`assemblyname`\>' contendo a definição para evento ' \<`eventname`\>'. Adicione uma referência ao seu projeto.  
  
 O evento é definido em uma biblioteca de vínculo dinâmico \(DLL\) ou assembly que não é referenciado diretamente em seu projeto. O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador requer uma referência para evitar ambigüidade, caso o evento é definido em mais de uma DLL ou assembly.  
  
 **ID do erro:** BC30005  
  
### Para corrigir este erro  
  
-   Inclua o nome da DLL ou assembly sem referência em suas referências do projeto.  
  
## Consulte também  
 [NIB: Referenciando Namespaces e componentes](http://msdn.microsoft.com/pt-br/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)