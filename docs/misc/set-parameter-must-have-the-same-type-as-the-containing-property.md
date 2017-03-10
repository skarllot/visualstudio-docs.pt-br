---
title: "O par&#226;metro &#39;Set&#39; deve ter o mesmo tipo da propriedade recipiente | Microsoft Docs"
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
  - "vbc31064"
  - "bc31064"
helpviewer_keywords: 
  - "BC31064"
ms.assetid: f0b8310d-68a1-4989-ac64-03b1861528ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O par&#226;metro &#39;Set&#39; deve ter o mesmo tipo da propriedade recipiente
O parâmetro para o `Set` procedimento de propriedade tem um tipo diferente da propriedade que pertence.  
  
 **ID do erro:** BC31064  
  
### Para corrigir este erro  
  
-   Altere o tipo de dados do parâmetro para `Set` para que ele corresponda ao tipo de dados para a propriedade. Por exemplo:  
  
    ```  
    Class Class1 ' Declare a local variable to hold the property value. Private Fval As Integer Property F() As Integer Get Return Fval End Get Set(ByVal Value As Integer) Fval = Value End Set End Property End Class  
    ```  
  
## Consulte também  
 [NÃO está em compilação: Como: adicionar campos e propriedades a uma classe](http://msdn.microsoft.com/pt-br/ae53f61b-3abc-413e-8931-703c5f5e8fc2)   
 [Procedimentos de propriedade](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [NÃO está em compilação: Propriedades e procedimentos de propriedade](http://msdn.microsoft.com/pt-br/23e2a1ec-7e9d-4109-8940-c703d981077b)