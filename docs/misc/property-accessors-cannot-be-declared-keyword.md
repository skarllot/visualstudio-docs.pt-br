---
title: "Acessadores de propriedade n&#227;o podem ser declarados como &#39;&lt; palavra-chave &gt;&#39; | Microsoft Docs"
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
  - "vbc31099"
  - "bc31099"
helpviewer_keywords: 
  - "BC31099"
ms.assetid: d6f3b989-39b9-4c47-995a-bd83ec03d7b8
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Acessadores de propriedade n&#227;o podem ser declarados como &#39;&lt; palavra-chave &gt;&#39;
Um `Get` ou `Set` declaração de procedimento inclui uma palavra\-chave não é válida em um procedimento de propriedade.  
  
 O [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement) e [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement) Permitir um modificador de acesso \(`Public`, `Protected`, `Friend`, `Protected Friend`, `Private`\).  
  
 **ID do erro:** BC31099  
  
### Para corrigir este erro  
  
-   Remova a palavra\-chave inválida da `Get` ou `Set` instrução.  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Como declarar uma propriedade com níveis de acesso mistos](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)