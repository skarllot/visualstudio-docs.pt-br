---
title: "Propriedade de membro de tipo an&#244;nimo &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser usada para inferir o tipo de outra propriedade de membro porque o tipo de &#39;&lt; propertyname &gt;&#39; ainda n&#227;o foi estabelecido | Microsoft Docs"
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
  - "vbc36559"
  - "bc36559"
helpviewer_keywords: 
  - "BC36559"
ms.assetid: 58ab8d35-9d85-4aca-8b4e-f232d7e4af61
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Propriedade de membro de tipo an&#244;nimo &#39;&lt; propertyname &gt;&#39; n&#227;o pode ser usada para inferir o tipo de outra propriedade de membro porque o tipo de &#39;&lt; propertyname &gt;&#39; ainda n&#227;o foi estabelecido
Até que o tipo de uma propriedade de tipo anônimo é estabelecido, ele não pode ser usado para estabelecer o tipo de outra propriedade. Por exemplo, na seguinte declaração `.IDName = .LastName` não é válido porque `.LastName` ainda não foi inicializado.  
  
```  
' Not valid.   
' Dim anon1 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}   
```  
  
 **ID do erro:** BC36559  
  
### Para corrigir este erro  
  
-   Estabeleça o tipo da propriedade antes de usá\-la para inicializar outra propriedade.  
  
    ```  
    Dim anon2 = New With {Key .LastName = "Jones", Key .IDName = .LastName}  
    ```  
  
## Consulte também  
 [Tipos anônimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)