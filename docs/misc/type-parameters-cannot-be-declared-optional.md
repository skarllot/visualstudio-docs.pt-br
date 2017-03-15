---
title: "par&#226;metros de &lt; tipo &gt; n&#227;o podem ser declarados &#39;Optional&#39; | Microsoft Docs"
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
  - "bc33010"
  - "vbc33010"
helpviewer_keywords: 
  - "BC33010"
ms.assetid: ec4023e7-9ba6-4532-a6b9-4ae6b4f9063a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# par&#226;metros de &lt; tipo &gt; n&#227;o podem ser declarados &#39;Optional&#39;
Uma definição de um delegado, um evento ou um operador declara um [Opcional](/dotnet/visual-basic/language-reference/modifiers/optional) parâmetro.  
  
 `Optional` parâmetros são permitidos apenas em `Declare`, `Function`, `Property`, e `Sub` parâmetros.  
  
 **ID do erro:** BC33010  
  
### Para corrigir este erro  
  
-   Remover o `Optional` palavra\-chave da lista de parâmetros.  
  
-   Se você estiver definindo um operador, você poderá obter o `Optional` funcionalidade com uma série de sobrecargas.  
  
-   Se você estiver definindo um evento ou delegado, você deve refazer a lógica geral dessa parte do seu aplicativo. Você não pode usar `Optional` ou [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray) parâmetros ou versões sobrecarregadas, nos parâmetros do delegado ou evento.  
  
## Consulte também  
 [Sobrecargas](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedimentos do operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Instrução Operator](/dotnet/visual-basic/language-reference/statements/operator-statement)