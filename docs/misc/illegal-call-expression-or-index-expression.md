---
title: "Express&#227;o ilegal de chamada ou &#237;ndice | Microsoft Docs"
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
  - "vbc32303"
  - "bc32303"
helpviewer_keywords: 
  - "BC32303"
ms.assetid: eed6a16e-4a44-4f72-b1de-d4212940da37
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Express&#227;o ilegal de chamada ou &#237;ndice
Um valor entre parênteses segue uma expressão que não é um procedimento, propriedade ou matriz.  
  
 O código a seguir pode gerar esse erro.  
  
 `Dim testVariable As Object = Nothing(1)`  
  
 Porque `Nothing` não não têm argumentos ou índices, você não pode usá\-lo com parênteses.  
  
 **ID do erro:** BC32303  
  
### Para corrigir este erro  
  
-   Remova os parênteses e qualquer valor que eles contêm.  
  
## Consulte também  
 [Como chamar um procedimento que retorna um valor](../Topic/How%20to:%20Call%20a%20Procedure%20That%20Returns%20a%20Value%20\(Visual%20Basic\).md)   
 [Como chamar um procedimento que não retorne um valor](../Topic/How%20to:%20Call%20a%20Procedure%20that%20Does%20Not%20Return%20a%20Value%20\(Visual%20Basic\).md)   
 [NOTINBUILD como: inserir um valor em uma matriz](http://msdn.microsoft.com/pt-br/6dddc79c-cf60-41c2-b572-8bfa49b4fe7e)   
 [NOTINBUILD como: obter um valor de uma matriz](http://msdn.microsoft.com/pt-br/202a6468-8ccb-4864-bd8b-eab3b42d4288)   
 [Como inserir um valor em uma propriedade](../Topic/How%20to:%20Put%20a%20Value%20in%20a%20Property%20\(Visual%20Basic\).md)   
 [Como obter um valor a partir de uma propriedade](../Topic/How%20to:%20Get%20a%20Value%20from%20a%20Property%20\(Visual%20Basic\).md)