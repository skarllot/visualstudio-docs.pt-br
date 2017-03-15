---
title: "O tipo &#39;&lt; typename &gt;&#39; n&#227;o pode ser usado como um atributo porque seu cont&#234;iner &#39;&lt; nomecont&#234;iner &gt;&#39; n&#227;o est&#225; declarado como &#39;Public&#39; | Microsoft Docs"
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
  - "bc31517"
  - "vbc31517"
helpviewer_keywords: 
  - "BC31517"
ms.assetid: 3d1a8f41-8652-4e37-a6bd-40b0ad306c6f
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; n&#227;o pode ser usado como um atributo porque seu cont&#234;iner &#39;&lt; nomecont&#234;iner &gt;&#39; n&#227;o est&#225; declarado como &#39;Public&#39;
A classe ou módulo onde esse atributo é definido não é declara usando o `Public` modificador. Classes e módulos que não especificam um modificador de acesso são declarados como `Friend` por padrão.  
  
 **ID do erro:** BC31517  
  
### Para corrigir este erro  
  
1.  Adicionar o `Public` modificador para a classe ou módulo onde esse atributo é definido.  
  
## Consulte também  
 [Público](/dotnet/visual-basic/language-reference/modifiers/public)