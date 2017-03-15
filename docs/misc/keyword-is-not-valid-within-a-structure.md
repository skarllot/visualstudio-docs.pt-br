---
title: "&#39;&lt; palavra-chave &gt;&#39; n&#227;o &#233; v&#225;lido dentro de uma estrutura | Microsoft Docs"
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
  - "bc30044"
  - "vbc30044"
helpviewer_keywords: 
  - "BC30044"
ms.assetid: 252510cf-e084-47e4-9592-4aa8f94fabe4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; palavra-chave &gt;&#39; n&#227;o &#233; v&#225;lido dentro de uma estrutura
Estruturas são tipos de valor, não tipos de referência. Uma estrutura não é uma instância criada a partir de uma classe, portanto, a `Me`, `MyClass`, e `MyBase` palavras\-chave fazem sentidas em uma estrutura.  
  
 **ID do erro:** BC30044  
  
### Para corrigir este erro  
  
-   Alterar a estrutura para uma classe, ou remova a palavra\-chave do procedimento.  
  
## Consulte também  
 [Me](http://msdn.microsoft.com/pt-br/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [MyClass \- excluir](http://msdn.microsoft.com/pt-br/5db36f9b-f796-4b6a-ba34-cac1fde6eb62)   
 [MyBase \- excluir](http://msdn.microsoft.com/pt-br/52491d06-6451-4f6f-9aa6-8fab59bbc2b9)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)