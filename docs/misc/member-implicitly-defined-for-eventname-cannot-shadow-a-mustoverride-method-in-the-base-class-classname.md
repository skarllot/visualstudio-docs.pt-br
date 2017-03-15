---
title: "&#39;&lt; membro &gt;&#39;, implicitamente definido para &#39;&lt; eventname &gt;&#39; n&#227;o pode sombrear um m&#233;todo &#39;MustOverride&#39; na base de &lt; classe &gt; &#39;&lt; classname &gt;&#39; | Microsoft Docs"
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
  - "vbc31413"
  - "bc31413"
helpviewer_keywords: 
  - "BC31413"
ms.assetid: 071706ce-a394-48b6-9afa-751cb50b2576
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; membro &gt;&#39;, implicitamente definido para &#39;&lt; eventname &gt;&#39; n&#227;o pode sombrear um m&#233;todo &#39;MustOverride&#39; na base de &lt; classe &gt; &#39;&lt; classname &gt;&#39;
O evento especificado declara implicitamente um membro com o mesmo nome de um método declarado com o `MustOverride` modificador.  
  
 **ID do erro:** BC31413  
  
### Para corrigir este erro  
  
-   Remover o `MustOverride` modificador do método na classe base ou dê a propriedade ou método um nome exclusivo.  
  
## Consulte também  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)