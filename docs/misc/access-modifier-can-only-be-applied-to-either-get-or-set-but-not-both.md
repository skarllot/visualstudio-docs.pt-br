---
title: "Modificador de acesso s&#243; pode ser aplicada para &#39;Get&#39; ou definir &#39;, mas n&#227;o ambos | Microsoft Docs"
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
  - "bc31101"
  - "vbc31101"
helpviewer_keywords: 
  - "BC31101"
ms.assetid: c2a0580c-ff2f-4cc9-9113-6e540f906eec
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Modificador de acesso s&#243; pode ser aplicada para &#39;Get&#39; ou definir &#39;, mas n&#227;o ambos
Uma declaração de propriedade especifica os níveis de acesso no [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement), o [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement), e o [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
 Você sempre pode especificar um nível de acesso para a propriedade. Além disso, você pode especificar um nível de acesso diferente para no máximo um dos seus procedimentos de propriedade \(`Get` ou `Set`\), desde que seja mais restritivo do que o nível de acesso da propriedade. É possível especificar níveis de acesso para ambos os procedimentos de propriedade.  
  
 **ID do erro:** BC31101  
  
### Para corrigir este erro  
  
-   Remova o modificador de acesso do `Get` instrução ou o `Set` instrução.  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)