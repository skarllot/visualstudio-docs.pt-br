---
title: "&#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a m&#233;todos &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "bc31531"
  - "vbc31531"
helpviewer_keywords: 
  - "BC31531"
ms.assetid: 0ea3a16c-cfe0-4cb5-b740-358679272f8d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;DllImportAttribute&#39; n&#227;o pode ser aplicado a m&#233;todos &#39;AddHandler&#39;, &#39;RemoveHandler&#39; ou &#39;RaiseEvent&#39;
O `DllImportAttribute` atributo foi aplicado a um `AddHandler`, `RemoveHandler`, ou `RaiseEvent` declaração de método. Esse atributo só pode ser usado com um vazio `Function` ou `Sub`.  
  
 **ID do erro:** BC31531  
  
### Para corrigir este erro  
  
-   Remover o `DllImportAttribute` atributo da declaração de método.  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- excluir](http://msdn.microsoft.com/pt-br/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- excluir](http://msdn.microsoft.com/pt-br/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- excluir](http://msdn.microsoft.com/pt-br/7f765da0-5491-40b6-9ed5-24c98f9daad9)