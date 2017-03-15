---
title: "As propriedades &#39;WriteOnly&#39; n&#227;o podem ter um modificador de acesso em &#39;Set&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31104"
  - "vbc31104"
helpviewer_keywords: 
  - "BC31104"
ms.assetid: d1ac04a8-e436-4f3e-8d71-fc4569b35fcd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# As propriedades &#39;WriteOnly&#39; n&#227;o podem ter um modificador de acesso em &#39;Set&#39;
Um `WriteOnly` declaração de propriedade especifica os níveis de acesso em ambos os [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement) e [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Você sempre pode especificar um nível de acesso para a propriedade. Além disso, você pode especificar um nível de acesso diferente para no máximo um dos seus procedimentos de propriedade \(`Get` ou `Set`\), desde que seja mais restritivo do que o nível de acesso da propriedade. É possível especificar níveis de acesso para ambos os procedimentos de propriedade.  
  
 **ID do erro:** BC31104  
  
### Para corrigir este erro  
  
-   Remova o modificador de acesso do `Set` instrução. Ele representa toda a `WriteOnly` propriedade e você não pode ter dois níveis de acesso para a propriedade.  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)