---
title: "O tipo &#39;&lt; typename &gt;&#39; no assembly &#39;&lt; assemblyname1 &gt;&#39; foi encaminhado ao assembly &#39;&lt; assemblyname2 &gt;&#39; | Microsoft Docs"
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
  - "vbc31424"
  - "bc31424"
helpviewer_keywords: 
  - "BC31424"
  - "encaminhamento de tipos"
ms.assetid: 0f53e613-c1cb-4722-acb5-afa3091e277b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo &#39;&lt; typename &gt;&#39; no assembly &#39;&lt; assemblyname1 &gt;&#39; foi encaminhado ao assembly &#39;&lt; assemblyname2 &gt;&#39;
O tipo '\< typename \>' no assembly '\< assemblyname1 \>' foi encaminhado ao assembly '\< assemblyname2 \>'. Ou uma referência a '\< assemblyname2 \>' está ausente do projeto ou o tipo '\< typename \>' está faltando no assembly '\< assemblyname2 \>'.  
  
 Uma expressão no código\-fonte para um assembly faz referência a um tipo que foi encaminhado para outro conjunto, mas o tipo não pode ser encontrado no assembly de destino.  
  
 *Encaminhamento de tipos* significa a reatribuição da definição de classe, estrutura, interface, representante ou enumeração a um assembly diferente no qual ele foi originalmente definido. Geralmente é usado em conjunto com *refatoração de código*, pelo qual você divide um assembly em dois ou mais assemblies ou mover o código de um assembly para outra.  
  
 Embora o tipo temporariamente ainda está disponível no conjunto original, é provável que se torne indefinido quando a refatoração de código remove do assembly original.  
  
 **ID do erro:** BC31424  
  
### Para corrigir este erro  
  
-   Verifique se que o tipo está presente no assembly de destino.  
  
-   Verifique se que seu projeto possui uma referência ao assembly de destino.  
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)