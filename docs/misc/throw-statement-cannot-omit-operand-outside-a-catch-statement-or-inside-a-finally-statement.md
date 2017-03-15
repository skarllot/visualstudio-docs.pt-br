---
title: "Instru&#231;&#227;o &#39;Throw&#39; n&#227;o pode omitir operando fora de uma instru&#231;&#227;o &#39;Catch&#39; ou dentro de uma instru&#231;&#227;o &#39;Finally&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30666"
  - "bc30666"
helpviewer_keywords: 
  - "BC30666"
ms.assetid: a208a6ea-0e36-4bf1-8984-4de1a0e38a2a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o &#39;Throw&#39; n&#227;o pode omitir operando fora de uma instru&#231;&#227;o &#39;Catch&#39; ou dentro de uma instru&#231;&#227;o &#39;Finally&#39;
`Throw` instruções fora do `Catch` instrução deve fornecer o nome de um objeto de exceção.  
  
 **ID do erro:** BC30666  
  
### Para corrigir este erro  
  
1.  Especifique o nome de um objeto de exceção derivado de `System.Exception`.  
  
2.  Reestruturar o código para que o `Throw` instrução está dentro de um `Catch` bloco.  
  
## Consulte também  
 [Instrução Throw](/dotnet/visual-basic/language-reference/statements/throw-statement)   
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Classe de exceção no Visual Basic](http://msdn.microsoft.com/pt-br/9aac396f-34ca-4afb-8e6c-e523cb690ba9)   
 [Exceção e tratamento de erros no Visual Basic](http://msdn.microsoft.com/pt-br/3e351e73-cf23-40ab-8b60-05794160529e)