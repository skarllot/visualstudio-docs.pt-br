---
title: "N&#227;o &#233; poss&#237;vel converter &#39;type1&#39; em &#39;type2&#39; | Microsoft Docs"
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
  - "bc31193"
  - "vbc31193"
helpviewer_keywords: 
  - "BC31193"
ms.assetid: f25a9f5b-7741-4cd6-b85a-b19037ed8e49
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel converter &#39;type1&#39; em &#39;type2&#39;
Não é possível converter 'type1' em 'type2'. Você pode usar a propriedade 'Value' para obter o valor de cadeia de caracteres do primeiro elemento de 'parentElement'.  
  
 Foi feita uma tentativa para converter implicitamente um literal XML para um tipo específico. O literal XML não pode ser convertido implicitamente no tipo especificado.  
  
 **ID do erro:** BC31193  
  
### Para corrigir este erro  
  
-   Use o `Value` propriedade do literal XML para referenciar seu valor como um `String`. Use o `CType` função, outra função de conversão de tipo, ou o <xref:System.Convert> classe para converter o valor do tipo especificado.  
  
## Consulte também  
 <xref:System.Convert>   
 [Acessando XML no Visual Basic](/dotnet/visual-basic/programming-guide/language-features/xml/accessing-xml)   
 [Funções de conversão do tipo](/dotnet/visual-basic/language-reference/functions/type-conversion-functions)   
 [Literais XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)