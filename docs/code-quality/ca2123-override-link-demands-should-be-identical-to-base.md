---
title: "CA2123: as demandas de link de substitui&#231;&#227;o devem ser id&#234;nticas &#224; base | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123: as demandas de link de substitui&#231;&#227;o devem ser id&#234;nticas &#224; base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um método protegido em um tipo substituem um método público ou implementam uma interface, e não tenham o mesmo [Demandas de link](../Topic/Link%20Demands.md) que a interface ou o método virtual.  
  
## Descrição da Regra  
 Esta regra um método corresponde ao método de base, que é uma interface ou um método virtual em outro tipo, e então compara as demandas de link em cada um.  Uma violação será informada se o método ou o método de base têm uma procura de link e outros não.  
  
 Se essa regra é violada, um chamador mal\-intencionado pode ignorar a procura de link simplesmente chamando o método não seguro.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, aplique a mesma procura de link para o método ou para a implementação de overide.  Se isso não for possível, marcar o método com uma procura completa ou remover completamente o atributo.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra mais violações desta regra.  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## Consulte também  
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)   
 [Demandas de link](../Topic/Link%20Demands.md)