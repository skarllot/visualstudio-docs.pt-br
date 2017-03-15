---
title: "Vari&#225;veis &#39;WithEvents&#39; s&#243; podem ser digitadas como classes, interfaces ou par&#226;metros de tipo com restri&#231;&#245;es de classe | Microsoft Docs"
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
  - "vbc30413"
  - "bc30413"
helpviewer_keywords: 
  - "BC30413"
ms.assetid: 11ddf207-2760-425f-b4c2-bb9fe6da36ea
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;veis &#39;WithEvents&#39; s&#243; podem ser digitadas como classes, interfaces ou par&#226;metros de tipo com restri&#231;&#245;es de classe
Você declarou uma variável digitada como uma estrutura em conjunto com `WithEvents`, que não é um uso válido do `WithEvents` modificador.  
  
 **ID do erro:** BC30413  
  
### Para corrigir este erro  
  
1.  Use `AddHandler` para manipular eventos definidos em uma estrutura.  
  
## Consulte também  
 [NÃO na compilação: WithEvents e a cláusula Handles](http://msdn.microsoft.com/pt-br/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Instrução AddHandler](/dotnet/visual-basic/language-reference/statements/addhandler-statement)