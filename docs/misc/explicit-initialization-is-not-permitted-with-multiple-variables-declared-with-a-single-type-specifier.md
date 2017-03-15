---
title: "Inicializa&#231;&#227;o expl&#237;cita n&#227;o &#233; permitida com v&#225;rias vari&#225;veis declaradas com um &#250;nico especificador de tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30671"
  - "vbc30671"
helpviewer_keywords: 
  - "BC30671"
ms.assetid: 57bbdd58-b58d-4144-8fa6-366a7167df27
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Inicializa&#231;&#227;o expl&#237;cita n&#227;o &#233; permitida com v&#225;rias vari&#225;veis declaradas com um &#250;nico especificador de tipo
Inicialização não é permitida quando múltiplas variáveis são declaradas na mesma linha.  
  
 **ID do erro:** BC30671  
  
### Para corrigir este erro  
  
1.  Declare e inicialize cada item separadamente.  
  
2.  Declare vários itens juntos e, em seguida, inicialize cada item; Por exemplo:  
  
    ```  
    Dim x, b, i As Integer x = 9 : b = 9 : i = 9 ' ":" is the same as a new line.  
    ```  
  
## Consulte também  
 [Instrução Dim](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [Declaração de variável](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)