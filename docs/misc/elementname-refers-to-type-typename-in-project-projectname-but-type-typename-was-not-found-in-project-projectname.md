---
title: "&#39;&lt; elementname &gt;&#39; se refere ao tipo &#39;&lt; typename &gt;&#39; no projeto &#39;&lt; projectname &gt;&#39;, mas o tipo &#39;&lt; typename &gt;&#39; n&#227;o foi encontrado no projeto &#39;&lt; projectname &gt;&#39; | Microsoft Docs"
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
  - "vbc30960"
  - "bc30960"
helpviewer_keywords: 
  - "BC30960"
ms.assetid: 4ed4bff5-c670-46f6-8360-7287444d50e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt; elementname &gt;&#39; se refere ao tipo &#39;&lt; typename &gt;&#39; no projeto &#39;&lt; projectname &gt;&#39;, mas o tipo &#39;&lt; typename &gt;&#39; n&#227;o foi encontrado no projeto &#39;&lt; projectname &gt;&#39;
Uma expressão acessa uma classe, estrutura, módulo ou interface que foram referidos em outro projeto, mas esse projeto não contém o tipo especificado.  
  
 Esse erro ocorre quando seu projeto faz uma referência indireta a outro projeto na mesma solução. Normalmente, seu projeto faz referência a um assembly que faz referência a outro projeto. Se a montagem acessa o tipo especificado no outro projeto, a referência indireta ao tipo é estabelecida. No entanto, se o tipo não está presente no outro projeto, esse erro será gerado.  
  
 **ID do erro:** BC30960  
  
### Para corrigir este erro  
  
-   Se o tipo citado não está definido em qualquer lugar, em seguida, remova ou substitua a declaração que tenta acessá\-lo. Você também precisará fazer a mesma alteração no assembly que faz a referência indireta ao tipo citado.  
  
-   Se o tipo citado é definido em qualquer lugar, em seguida, fazer uma referência direta ao projeto ou assembly que o define.  
  
## Consulte também  
 [NIB: Referenciando Namespaces e componentes](http://msdn.microsoft.com/pt-br/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Gerenciando referências em um projeto](../ide/managing-references-in-a-project.md)   
 [PONTA: Referências](http://msdn.microsoft.com/pt-br/910912ce-0dc9-4569-9274-32c44a20cb2c)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)