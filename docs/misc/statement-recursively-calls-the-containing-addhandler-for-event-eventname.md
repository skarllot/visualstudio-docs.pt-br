---
title: "A instru&#231;&#227;o chama recursivamente o recipiente &#39;AddHandler&#39; para evento &#39;&lt; eventname &gt;&#39; | Microsoft Docs"
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
  - "bc41998"
  - "vbc41998"
helpviewer_keywords: 
  - "BC41998"
ms.assetid: 4375b191-fbd9-4e93-b9bb-9159d533ddf6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# A instru&#231;&#227;o chama recursivamente o recipiente &#39;AddHandler&#39; para evento &#39;&lt; eventname &gt;&#39;
As instruções de `AddHandler` acessador de uma definição de eventos não deve referência de eventos diretamente.  
  
 A abordagem recomendada é armazenar a lista de manipuladores de eventos do como um campo particular na classe, estrutura ou módulo que definiu o evento. Para obter mais informações, consulte [Como declarar eventos personalizados para evitar bloqueio](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md) e [Como declarar eventos personalizados para conservar memória](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md).  
  
 **ID do erro:** BC41998  
  
### Para corrigir este erro  
  
-   Reescreva a definição do evento para evitar a recursão.  
  
## Consulte também  
 [AddHandler \- excluir](http://msdn.microsoft.com/pt-br/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [Instrução Event](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Como declarar eventos personalizados para evitar bloqueio](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [Como declarar eventos personalizados para conservar memória](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)