---
title: "&#39;&lt; nome do membro &gt;&#39; n&#227;o &#233; um membro de &#39;&lt; contextname &gt;&#39;; ele n&#227;o existe no contexto atual | Microsoft Docs"
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
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; nome do membro &gt;&#39; n&#227;o &#233; um membro de &#39;&lt; contextname &gt;&#39;; ele n&#227;o existe no contexto atual
Um nome de membro inexistente foi atribuído a uma propriedade em uma declaração de tipo anônimo. No exemplo a seguir, `.Prop1` e `.Prop2` são as propriedades do tipo anônimo. Tentativa de atribuir `.Prop3` para `.Prop2` causa o erro.  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **ID do erro:** BC36657  
  
### Para corrigir este erro  
  
-   Examine seu código para determinar o que você deseja atribuir. O nome da variável pode estar incorreto ou pode exigir qualificação se é uma propriedade de outro objeto.  
  
## Consulte também  
 [Tipos anônimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)