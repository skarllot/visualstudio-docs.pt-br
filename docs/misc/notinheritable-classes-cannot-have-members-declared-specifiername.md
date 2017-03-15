---
title: "Classes &#39;NotInheritable&#39; n&#227;o podem ter membros declarados &#39;&lt; specifiername &gt;&#39; | Microsoft Docs"
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
  - "vbc30607"
  - "bc30607"
helpviewer_keywords: 
  - "BC30607"
ms.assetid: c800e24e-d055-402f-b378-6d2f4041ff16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classes &#39;NotInheritable&#39; n&#227;o podem ter membros declarados &#39;&lt; specifiername &gt;&#39;
Modificadores de substituição não podem ser usadas com `NotInheritable` classes porque seus membros não podem ser substituídos.  
  
 **ID do erro:** BC30607  
  
### Para corrigir este erro  
  
-   Remova os modificadores de substituição, como `Overridable`, `NotOverridable`, ou `MustOverride`, da definição de classe.  
  
## Consulte também  
 [Substituível](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [NÃO está em compilação: Substituindo métodos e propriedades](http://msdn.microsoft.com/pt-br/2167e8f5-1225-4b13-9ebd-02591ba90213)