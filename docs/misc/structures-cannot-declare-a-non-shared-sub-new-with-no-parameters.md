---
title: "Estruturas n&#227;o podem declarar &#39;Sub New&#39; n&#227;o compartilhado sem par&#226;metros | Microsoft Docs"
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
  - "vbc30629"
  - "bc30629"
helpviewer_keywords: 
  - "BC30629"
ms.assetid: f4298ef7-85b1-4543-b764-4c3abda84baa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Estruturas n&#227;o podem declarar &#39;Sub New&#39; n&#227;o compartilhado sem par&#226;metros
`Sub New` construtores declarados dentro de estruturas deve aceitar argumentos ou ser declarados com o `Shared` modificador.  
  
 **ID do erro:** BC30629  
  
### Para corrigir este erro  
  
-   Alterar o `Sub New` para que ele aceita argumentos de construtor.  
  
-   Aplicar o `Shared` modificador para tornar o construtor compartilhado.  
  
## Consulte também  
 [Instrução Structure](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Estruturas](/dotnet/visual-basic/programming-guide/language-features/data-types/structures)