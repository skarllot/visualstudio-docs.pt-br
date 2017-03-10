---
title: "Refer&#234;ncia necess&#225;ria para o m&#243;dulo &#39;&lt; modulename &gt;&#39; que cont&#233;m a interface implementada &#39;&lt; interfacename &gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30010"
  - "bc30010"
helpviewer_keywords: 
  - "BC30010"
ms.assetid: 57fe7e15-bf99-49d1-ba6c-bb7abeb615b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncia necess&#225;ria para o m&#243;dulo &#39;&lt; modulename &gt;&#39; que cont&#233;m a interface implementada &#39;&lt; interfacename &gt;&#39;
Referência necessária para o módulo '\< modulename \>' que contém a interface implementada '\< interfacename \>'. Adicione uma ao seu projeto.  
  
 A interface é definida em um módulo que não é referenciado diretamente em seu projeto. O [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilador requer uma referência para evitar ambigüidade, caso a interface é definida em mais de um módulo.  
  
 **ID do erro:** BC30010  
  
### Para corrigir este erro  
  
-   Inclua o nome do módulo sem referência em suas referências do projeto.  
  
## Consulte também  
 [NIB: Referenciando Namespaces e componentes](http://msdn.microsoft.com/pt-br/568fa759-796b-44cd-bf5e-1cf8de6e38fd)   
 [Solucionando Problemas de Referências Quebradas](../ide/troubleshooting-broken-references.md)