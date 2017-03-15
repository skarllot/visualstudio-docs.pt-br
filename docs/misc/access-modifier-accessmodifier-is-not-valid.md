---
title: "Modificador de acesso &#39;&lt; accessmodifier &gt;&#39; n&#227;o &#233; v&#225;lido | Microsoft Docs"
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
  - "bc31100"
  - "vbc31100"
helpviewer_keywords: 
  - "BC31100"
ms.assetid: 1cd71acc-0b54-4f64-8d61-75b272d293cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Modificador de acesso &#39;&lt; accessmodifier &gt;&#39; n&#227;o &#233; v&#225;lido
Um [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement) ou [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement) Especifica um nível de acesso que é menos restritivo que o especificado para a propriedade recipiente.  
  
 Você sempre pode especificar um nível de acesso para a propriedade. Além disso, você pode especificar um nível de acesso diferente para no máximo um dos seus procedimentos de propriedade \(`Get` ou `Set`\), desde que seja mais restritivo do que o nível de acesso da propriedade. Por exemplo, se a propriedade for `Friend`, você pode especificar `Private` para um procedimento de propriedade, mas não `Public`. É possível especificar níveis de acesso para ambos os procedimentos de propriedade.  
  
 **ID do erro:** BC31100  
  
### Para corrigir este erro  
  
-   Verifique o nível de acesso para o procedimento de propriedade mais restritivo do que para a propriedade, ou remova o modificador de acesso inteiramente.  
  
-   Declare o acesso menos restritivo nível de [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement), e declare o nível de acesso mais restritivo em um dos procedimentos de propriedade.  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)