---
title: "Propriedades &#39;ReadOnly&#39; n&#227;o podem ter um modificador de acesso em &#39;Get&#39; | Microsoft Docs"
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
  - "vbc31105"
  - "bc31105"
helpviewer_keywords: 
  - "BC31105"
ms.assetid: 54066d8e-eb22-4b99-bb18-45afe61d3b33
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedades &#39;ReadOnly&#39; n&#227;o podem ter um modificador de acesso em &#39;Get&#39;
Um `ReadOnly` declaração de propriedade especifica os níveis de acesso em ambos os [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement) e [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement).  
  
 Você sempre pode especificar um nível de acesso para a propriedade. Além disso, você pode especificar um nível de acesso diferente para no máximo um dos seus procedimentos de propriedade \(`Get` ou `Set`\), desde que seja mais restritivo do que o nível de acesso da propriedade. É possível especificar níveis de acesso para ambos os procedimentos de propriedade.  
  
 **ID do erro:** BC31105  
  
### Para corrigir este erro  
  
-   Remova o modificador de acesso do `Get` instrução. Ele representa toda a `ReadOnly` propriedade e você não pode ter dois níveis de acesso para a propriedade.  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)