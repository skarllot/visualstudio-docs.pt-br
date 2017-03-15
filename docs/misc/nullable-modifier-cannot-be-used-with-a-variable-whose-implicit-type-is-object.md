---
title: "Modificador anul&#225;vel n&#227;o pode ser usado com uma vari&#225;vel cujo tipo impl&#237;cito &#233; &#39;Object&#39; | Microsoft Docs"
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
  - "bc33112"
  - "vbc33112"
helpviewer_keywords: 
  - "BC33112"
ms.assetid: 50b2a2ad-248d-4faa-820d-bcdf0e8b4aad
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Modificador anul&#225;vel n&#227;o pode ser usado com uma vari&#225;vel cujo tipo impl&#237;cito &#233; &#39;Object&#39;
Uma declaração de variável inclui o modificador de tipo anulável \(?\), mas não especificar um tipo ou inferir um tipo atribuindo um valor à variável declarada.  
  
 **ID do erro:** BC33112  
  
### Para corrigir este erro  
  
-   Especifique um tipo quando declarar a variável anulável. O tipo não pode ser <xref:System.Object>.  
  
-   Atribua um valor quando declarar a variável anulável. O tipo de variável anulável será inferido do valor atribuído. O tipo de valor não pode ser <xref:System.Object>.  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)