---
title: "&lt; erro &gt;: &#39;&lt; constructorname1 &gt;&#39; chama &#39;&lt; constructorname2 &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30297"
  - "bc30297"
helpviewer_keywords: 
  - "BC30297"
ms.assetid: dfca67d7-f4d7-4451-a937-68f22b8527d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt; erro &gt;: &#39;&lt; constructorname1 &gt;&#39; chama &#39;&lt; constructorname2 &gt;&#39;
Ocorre uma chamada de construtor circular. Um construtor faz uma chamada para `Me.New()` ou `MyClass.New()`. Uma causa possível é uma tentativa de chamar um construtor sobrecarregado com uma lista de argumentos diferentes.  
  
 **ID do erro:** BC30297  
  
### Para corrigir este erro  
  
-   Use uma lista de argumentos diferentes para chamar um construtor sobrecarregado.  
  
-   Se não houver nenhuma das sobrecargas acessível, remova a chamada para `Me.New()` ou `MyClass.New()`.  
  
## Consulte também  
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)