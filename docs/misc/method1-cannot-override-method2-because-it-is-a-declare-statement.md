---
title: "&#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque ela &#233; uma instru&#231;&#227;o &#39;Declare&#39; | Microsoft Docs"
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
  - "vbc30474"
  - "bc30474"
helpviewer_keywords: 
  - "BC30474"
ms.assetid: 7277e8cc-aa3c-40c3-8682-c8c42d2ee921
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque ela &#233; uma instru&#231;&#227;o &#39;Declare&#39;
Você tentou desautorizar um delegado no nome da classe base que foi declarado com um `Declare` instrução.  
  
 **ID do erro:** BC30474  
  
### Para corrigir este erro  
  
1.  Altere o membro substituído, portanto, não é um `Declare` instrução.  
  
2.  Não tente substituir esse método.  
  
## Consulte também  
 [Instrução Declare](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)