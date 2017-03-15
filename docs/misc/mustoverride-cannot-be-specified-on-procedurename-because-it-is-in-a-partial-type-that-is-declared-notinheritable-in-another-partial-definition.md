---
title: "&#39;MustOverride&#39; n&#227;o pode ser especificado em &#39;&lt; procedurename &gt;&#39; porque ele est&#225; em um parcial tipo declarado &#39;NotInheritable&#39; em outra defini&#231;&#227;o parcial | Microsoft Docs"
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
  - "vbc30927"
  - "BC30927"
helpviewer_keywords: 
  - "BC30927"
ms.assetid: 5798dfda-3d7b-4f30-9715-40cbf52d6dc4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;MustOverride&#39; n&#227;o pode ser especificado em &#39;&lt; procedurename &gt;&#39; porque ele est&#225; em um parcial tipo declarado &#39;NotInheritable&#39; em outra defini&#231;&#227;o parcial
Um procedimento ou propriedade é declarada como `MustOverride` dentro de uma classe que é definida em várias declarações parciais, mas uma das definições parciais especifica `NotInheritable` para a classe.  
  
 Quando você divide a definição de uma classe entre várias declarações parciais, o compilador trata a classe como a união de todas as suas declarações parciais. Isso se aplica não apenas aos membros mas também para a implementação, herança e nível de acesso.  
  
 Para substituir um procedimento ou uma propriedade, uma classe deve herdá\-la de uma classe base. Portanto, para especificar `MustOverride` para um procedimento ou propriedade em uma classe base, você deve especificar `MustInherit` para a classe. Como eles são mutuamente contraditórios, não é possível especificar `MustInherit` e `NotInheritable` para a mesma classe.  
  
 **ID do erro:** BC30927  
  
### Para corrigir este erro  
  
-   Se a propriedade ou procedimento deve ser substituído, remova o `NotInheritable` palavra\-chave da declaração parcial na qual ele aparece.  
  
-   Se a classe deve ser `NotInheritable`, em seguida, remova o `MustOverride` palavra\-chave do procedimento ou propriedade. Você não pode substituí\-la porque você não pode herdar a classe.  
  
## Consulte também  
 [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Noções básicas de herança](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)