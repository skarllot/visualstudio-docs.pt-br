---
title: "A instru&#231;&#227;o n&#227;o declara um m&#233;todo &#39;Get&#39; ou &#39;Set&#39; | Microsoft Docs"
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
  - "bc30576"
  - "vbc30576"
helpviewer_keywords: 
  - "BC30576"
ms.assetid: 0f5aabd8-7cd0-4eaa-ae92-67be260cf63e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A instru&#231;&#227;o n&#227;o declara um m&#233;todo &#39;Get&#39; ou &#39;Set&#39;
Sua instrução falha ao não fornecer uma um `Get` ou `Set` em torno de uma instrução de declaração uma `Property` procedimento. Uma propriedade é definida como um bloco de código entre o `Property` e `End Property` instruções. Dentro deste bloco, cada `Property` procedimento aparece como um bloco interno envolto em uma instrução de declaração e uma instrução end.  
  
 **ID do erro:** BC30576  
  
### Para corrigir este erro  
  
-   Fornecer um `Get` ou `Set` uma instrução de declaração.  
  
## Consulte também  
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)