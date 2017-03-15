---
title: "N&#227;o &#233; poss&#237;vel chamar a fun&#231;&#227;o friend no objeto que n&#227;o &#233; uma inst&#226;ncia de defini&#231;&#227;o de classe | Microsoft Docs"
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
  - "vbrID97"
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel chamar a fun&#231;&#227;o friend no objeto que n&#227;o &#233; uma inst&#226;ncia de defini&#231;&#227;o de classe
Ou você tentou chamar o `Friend` procedimento de uma classe, ou você tentou acessar uma `Friend` propriedade ou método entre processos ou entre threads. Um `Friend` procedimento pode ser chamado a partir de um módulo fora da classe, mas faz parte do projeto no qual a classe é definida.  
  
### Para corrigir este erro  
  
-   Certifique\-se de que você está chamando ou acessando o procedimento de um módulo que faz parte do projeto no qual a classe é definida.  
  
## Consulte também  
 [Friend](/dotnet/visual-basic/language-reference/modifiers/friend)