---
title: "Refer&#234;ncia ao objeto em constru&#231;&#227;o n&#227;o &#233; v&#225;lida ao chamar outro construtor | Microsoft Docs"
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
  - "bc31095"
  - "vbc31095"
helpviewer_keywords: 
  - "BC31095"
ms.assetid: 68be49f1-e662-45c7-9998-e0006324535d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia ao objeto em constru&#231;&#227;o n&#227;o &#233; v&#225;lida ao chamar outro construtor
Uma referência foi feita para um membro objeto antes que o construtor do objeto terminar de criar o objeto.  
  
 **ID do erro:** BC31095  
  
### Para corrigir este erro  
  
-   Não use `MyBase`, `MyClass`, ou `Me` ao chamar um construtor a partir de outro construtor.  
  
## Consulte também  
 [Tempo de vida do objeto: como os objetos são criados e destruídos](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)   
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/pt-br/548eebe1-86c4-4377-b2f5-447cb8be3d90)