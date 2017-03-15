---
title: "&#39;End Get&#39; deve ser precedido por &#39;Get&#39; correspondente | Microsoft Docs"
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
  - "bc30630"
  - "vbc30630"
helpviewer_keywords: 
  - "BC30630"
ms.assetid: d858076a-9088-4ad0-9766-95029476bf9b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Get&#39; deve ser precedido por &#39;Get&#39; correspondente
`End Get` é usado para finalizar `Get` procedimentos de propriedade. O `End Get` construção foi encontrada fora de uma `Get` procedimento de propriedade.  
  
 **ID do erro:** BC30630  
  
### Para corrigir este erro  
  
1.  Verifique se o `Get` procedimento de propriedade é declarado após um `Property` palavra\-chave e antes do `End Property` Construir.  
  
2.  Verifique se o `Get` procedimento de propriedade começa com o `Get` palavra\-chave e termina com `End Get` Construir.  
  
## Consulte também  
 [Instrução Property](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Property Changes in Visual Basic](http://msdn.microsoft.com/pt-br/1c138efa-9bc2-44d7-80a0-f3a7c2510264)