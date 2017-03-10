---
title: "&#39;&lt; typename &gt;&#39; no assembly &#39;&lt; assemblyname &gt;&#39; foi encaminhado para si mesmo e, portanto, &#233; um tipo sem suporte | Microsoft Docs"
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
  - "bc31425"
  - "vbc31425"
helpviewer_keywords: 
  - "BC31425"
  - "encaminhamento de tipos"
ms.assetid: e3275d55-3f4c-4bbc-9c8f-f55c4e973063
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; typename &gt;&#39; no assembly &#39;&lt; assemblyname &gt;&#39; foi encaminhado para si mesmo e, portanto, &#233; um tipo sem suporte
Um assembly usa a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> para encaminhar um de seus tipos para outro conjunto, mas Especifica o mesmo tipo no mesmo assembly.  
  
 *Encaminhamento de tipos* significa a reatribuição da definição de classe, estrutura, interface, representante ou enumeração a um assembly diferente no qual ele foi originalmente definido. Geralmente é usado em conjunto com *refatoração de código*, pelo qual você divide um assembly em dois ou mais assemblies ou mover o código de um assembly para outra.  
  
 Encaminhamento de um tipo a mesmo resulta em encaminhamento circular. Se outro assembly tentou acessar o tipo encaminhado, ele seria passar por interminável encaminhamento sem nunca chegar a um tipo que não tinha sido encaminhado.  
  
 **ID do erro:** BC31425  
  
### Para corrigir este erro  
  
-   Encaminhar o tipo para um tipo em um assembly diferente ou não encaminhe todo.  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)