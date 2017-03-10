---
title: "par&#226;metros de &lt; tipo &gt; n&#227;o podem ser declarados como &#39;ParamArray&#39; | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# par&#226;metros de &lt; tipo &gt; n&#227;o podem ser declarados como &#39;ParamArray&#39;
Uma definição de um delegado, um evento ou um operador declara um [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray) parâmetro.  
  
 `ParamArray` parâmetros são permitidos apenas em `Declare`, `Function`, `Property`, e `Sub` parâmetros.  
  
 **ID do erro:** BC33009  
  
### Para corrigir este erro  
  
-   Remover o `ParamArray` palavra\-chave da lista de parâmetros.  
  
-   Se você estiver definindo um operador, você poderá obter o `ParamArray` funcionalidade com uma série de sobrecargas.  
  
-   Se você estiver definindo um evento ou delegado, você deve refazer a lógica geral dessa parte do seu aplicativo. Você não pode usar [Opcional](/dotnet/visual-basic/language-reference/modifiers/optional) ou `ParamArray` parâmetros ou versões sobrecarregadas, nos parâmetros do delegado ou evento.  
  
## Consulte também  
 [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)