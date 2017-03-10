---
title: "N&#227;o foi poss&#237;vel determinar se &#39;assembly&#39; &#233; um assembly de v&#225;rios arquivos. O manifesto do assembly pode estar corrompido. Supondo que um assembly n&#227;o multiarquivo. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.unknownscatterstatusforcopy"
ms.assetid: be49d3f2-b091-488c-8579-e27ef09d9c80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel determinar se &#39;assembly&#39; &#233; um assembly de v&#225;rios arquivos. O manifesto do assembly pode estar corrompido. Supondo que um assembly n&#227;o multiarquivo.
O sistema do projeto não pôde ler um assembly referenciado por seu projeto, de modo que o sistema do projeto é incapaz de determinar se você está fazendo referência a um assembly de vários arquivos. Portanto, o assembly pode não ser copiado corretamente para o diretório de saída.  
  
 **Para corrigir este erro**  
  
-   Reinstale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(se o assembly acompanha [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou o .NET Framework\).  
  
     \- ou \-  
  
-   Reinstale o controle apropriado de terceiros.  
  
     Esse erro não impedirá que o projeto seja criada. No entanto, um erro de tempo de execução é possível.  
  
## Consulte também  
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)   
 [PONTA como: Adicionar ou remover referências usando a caixa de diálogo Adicionar referência](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/pt-br/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)