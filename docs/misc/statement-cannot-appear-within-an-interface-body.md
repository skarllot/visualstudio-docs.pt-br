---
title: "Instru&#231;&#227;o n&#227;o pode aparecer no corpo de uma interface | Microsoft Docs"
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
  - "vbc30603"
  - "BC30603"
helpviewer_keywords: 
  - "BC30603"
ms.assetid: 3aef29d6-eadf-4f1f-b214-dfeae5e51c4f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o n&#227;o pode aparecer no corpo de uma interface
A declaração de um membro de interface inclui uma declaração terminando o membro, do formulário `End` *membername*.  
  
 Uma interface define somente a assinatura de seus membros. Consequentemente, procedimentos e propriedades definidas em uma interface tem somente sua linha inicial, especificando o nome e assinatura. Você não inclui nenhum código, declarações internas, ou um `End Function`, `End Property`, ou `End Sub` instrução dentro da interface.  
  
 **ID do erro:** BC30603  
  
### Para corrigir este erro  
  
-   Remover o `End` *membername* instrução de definição de interface.  
  
## Consulte também  
 [Instrução Interface](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Instrução End \<keyword\>](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)