---
title: "&#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque eles diferem em seus tipos de retorno | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30437"
  - "vbc30437"
helpviewer_keywords: 
  - "BC30437"
ms.assetid: e566ae72-c597-4b33-b70d-5d4ea879d644
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; method1 &gt;&#39; n&#227;o pode substituir &#39;&lt; method2 &gt;&#39; porque eles diferem em seus tipos de retorno
Você tentou substituir um método com outro método que difere em seu tipo de retorno. Um tipo pode substituir um método substituível herdado, declarando um método com o mesmo nome e assinatura e marcando a declaração com o `Overrides` modificador. As assinaturas dos dois métodos devem corresponder.  
  
 **ID do erro:** BC30437  
  
### Para corrigir este erro  
  
-   Verifique os tipos de retorno dos métodos e alterá\-los conforme necessário para fazer a correspondência.  
  
## Consulte também  
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)