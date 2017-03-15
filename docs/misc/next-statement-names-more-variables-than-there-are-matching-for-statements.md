---
title: "Instru&#231;&#227;o &#39;Next&#39; nomeia mais vari&#225;veis do que &#39;instru&#231;&#245;es For&#39; correspondente | Microsoft Docs"
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
  - "bc32037"
  - "vbc32037"
helpviewer_keywords: 
  - "BC32037"
ms.assetid: 7c97d835-1043-40ec-a645-63a053f5f916
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o &#39;Next&#39; nomeia mais vari&#225;veis do que &#39;instru&#231;&#245;es For&#39; correspondente
Loops aninhadas terminam com uma única `Next` instrução que especifica mais loop variáveis que os loops in a aninhada, como no exemplo a seguir:  
  
```  
For I = 1 To 10 For J = 1 To 5 ' ... Next J, I, K   ' Next J, I is valid, but there is no loop on K.  
```  
  
 **ID do erro:** BC32037  
  
### Para corrigir este erro  
  
1.  Verifique se o `Next` declaração especifica todas as variáveis loop aninhadas na ordem inversa de loop inicial.  
  
2.  Remova quaisquer variáveis estranhas de `Next` instrução.  
  
## Consulte também  
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)