---
title: "Express&#227;o &#39;AddressOf&#39; n&#227;o pode ser convertido em &#39;&lt; typename &gt;&#39; porque o tipo &#39;&lt; typename &gt;&#39; &#233; declarado &#39;MustInherit&#39; e n&#227;o pode ser criado | Microsoft Docs"
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
  - "vbc30939"
  - "bc30939"
helpviewer_keywords: 
  - "BC30939"
ms.assetid: e8edef15-0df5-46d7-aba6-89e26a2aa506
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o &#39;AddressOf&#39; n&#227;o pode ser convertido em &#39;&lt; typename &gt;&#39; porque o tipo &#39;&lt; typename &gt;&#39; &#233; declarado &#39;MustInherit&#39; e n&#227;o pode ser criado
Uma instrução tenta converter um `AddressOf` expressão em um tipo que só pode ser uma classe base e não pode ser usado para criar uma instância.  
  
 O `AddressOf` operador cria uma instância delegada de procedimento que faz referência a um procedimento específico.  
  
 **ID do erro:** BC30939  
  
### Para corrigir este erro  
  
-   Atribuir o `AddressOf` expressão em um tipo de delegado específico.  
  
## Consulte também  
 [Operador AddressOf](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [NÃO está em compilação: Delegados e o operador AddressOf](http://msdn.microsoft.com/pt-br/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)