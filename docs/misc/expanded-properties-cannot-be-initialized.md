---
title: "N&#227;o n&#227;o poss&#237;vel inicializar propriedades expandidas | Microsoft Docs"
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
  - "vbc36714"
  - "bc36714"
helpviewer_keywords: 
  - "BC36714"
ms.assetid: ba9408f3-e606-4749-8372-987999f405f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# N&#227;o n&#227;o poss&#237;vel inicializar propriedades expandidas
Uma propriedade implementada automaticamente pode ser inicializada como parte de sua declaração, mas não pode ser uma propriedade expandida.  
  
 **ID do erro:** BC36714  
  
### Para corrigir este erro  
  
-   Use uma propriedade implementada automaticamente ou remova a inicialização da declaração de propriedade.  
  
## Exemplo  
 Os exemplos a seguir mostram ambas autoimplementadas e expandido de propriedades. Propriedades autoimplementadas podem ser inicializadas usando a atribuição ou um `New` não podem ser a cláusula, mas as propriedades expandidas.  
  
```vb#  
Class AutoImplementedExample ' An auto-implemented property can be assigned an initial value. Property IDNum As Integer = 33542 ' An auto-implemented property can be initialized with New. Property Name As New String("Don Hall") End Class Class ExpandedExample ' Attempting to expand an initialized auto-implemented property ' causes this error. 'Property IDNum As Integer = 33542 '    Get '    End Get '    Set(ByVal value As Integer) '    End Set 'End Property ' Instead, you can assign the initial value to the backing field. Private _IDNum As Integer = 33542 Property IDNum As Integer Get End Get Set(ByVal value As Integer) End Set End Property End Class  
```  
  
## Consulte também  
 [Propriedades autoimplementadas](/dotnet/visual-basic/programming-guide/language-features/procedures/auto-implemented-properties)   
 [Como criar uma propriedade](../Topic/How%20to:%20Create%20a%20Property%20\(Visual%20Basic\).md)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)