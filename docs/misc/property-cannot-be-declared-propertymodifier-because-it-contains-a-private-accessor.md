---
title: "Propriedade n&#227;o pode ser declarada &#39;&lt; propertymodifier &gt;&#39; porque ela cont&#233;m um acessador &#39;Private&#39; | Microsoft Docs"
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
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade n&#227;o pode ser declarada &#39;&lt; propertymodifier &gt;&#39; porque ela cont&#233;m um acessador &#39;Private&#39;
Uma propriedade com um `Private` procedimento de propriedade \(`Get` ou `Set`\) está marcado como [Substituível](/dotnet/visual-basic/language-reference/modifiers/overridable).  
  
 Se uma propriedade de classe base ou um procedimento é declarado [Particular](/dotnet/visual-basic/language-reference/modifiers/private), uma classe derivada não pode substituir essa propriedade ou procedimento porque ele não pode acessá\-lo. Por isso, você não pode usar `Private` em combinação com `Overridable`. Isso se aplica não apenas a própria propriedade, mas também os procedimentos de propriedade individual.  
  
 **ID do erro:** BC31108  
  
### Para corrigir este erro  
  
-   Remover o `Overridable` palavra\-chave from a [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement), ou remover o `Private` palavra\-chave from a [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement) ou [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)