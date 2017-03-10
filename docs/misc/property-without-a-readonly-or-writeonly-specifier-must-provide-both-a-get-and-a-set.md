---
title: "Propriedade sem um especificador &#39;ReadOnly&#39; ou &#39;WriteOnly&#39; deve fornecer &#39;Get&#39; e &#39;Set&#39; | Microsoft Docs"
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
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade sem um especificador &#39;ReadOnly&#39; ou &#39;WriteOnly&#39; deve fornecer &#39;Get&#39; e &#39;Set&#39;
Se uma propriedade não é declarada como `ReadOnly` ou `WriteOnly`, ele deve fornecer os procedimentos para ler e gravar o seu valor.  
  
 **ID do erro:** BC30124  
  
### Para corrigir este erro  
  
1.  Verifique se você incluir uma `Get` procedimento e uma `Set` procedimento entre o `Property` instrução e `End Property` instrução.  
  
2.  Verifique se que outros procedimentos dentro do `Property` declaração são terminadas corretamente.  
  
## Consulte também  
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Instrução Get](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Instrução Set](/dotnet/visual-basic/language-reference/statements/set-statement)