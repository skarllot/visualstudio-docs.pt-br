---
title: "N&#227;o &#233; poss&#237;vel especificar o modificador anul&#225;vel nas declara&#231;&#245;es de vari&#225;vel com &#39;As New&#39; | Microsoft Docs"
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
  - "bc33109"
  - "vbc33109"
helpviewer_keywords: 
  - "BC33109"
ms.assetid: 135def20-3535-4239-bffb-43208d1b3f63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o &#233; poss&#237;vel especificar o modificador anul&#225;vel nas declara&#231;&#245;es de vari&#225;vel com &#39;As New&#39;
O modificador de tipo anulável \(?\) foi incluído em uma declaração de variável onde `As New` foi especificado. O exemplo a seguir causa esse erro:  
  
```vb#  
Dim num? As New ExampleStructure  
```  
  
 **ID do erro:** BC33109  
  
### Para corrigir este erro  
  
1.  Remover o `New` palavra\-chave da declaração da variável anulável, conforme mostrado no exemplo a seguir:  
  
    ```vb#  
    Dim num? As ExampleStructure  
    ```  
  
## Consulte também  
 [Tipos de valor que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)