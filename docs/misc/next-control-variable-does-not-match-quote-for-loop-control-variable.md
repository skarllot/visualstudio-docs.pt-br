---
title: "Vari&#225;vel de controle &#39;Next&#39; n&#227;o coincide com &#39;vari&#225;vel de controle de loop For&#39; | Microsoft Docs"
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
  - "vbc30976"
  - "bc30976"
helpviewer_keywords: 
  - "BC30976"
ms.assetid: 87c2d464-43bf-426f-b78b-7bc07ba171e6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Vari&#225;vel de controle &#39;Next&#39; n&#227;o coincide com &#39;vari&#225;vel de controle de loop For&#39;
A variável de controle no `Next` declaração de um `For...Next` loop deve coincidir com a variável no correspondente `For` instrução.  
  
 **ID do erro:** BC30976  
  
### Para corrigir este erro  
  
-   Verifique a ortografia da variável no `Next` instrução in correspondente e `For` instrução para verificar se ela corresponde.  
  
-   Certifique\-se de que nenhuma parte do loop delimitador tenha sido excluída acidentalmente.  
  
-   Se este loop for parte de um conjunto de loops aninhados, certifique\-se de que cada loop está terminado corretamente.  
  
## Consulte também  
 [Instrução For...Next](/dotnet/visual-basic/language-reference/statements/for-next-statement)