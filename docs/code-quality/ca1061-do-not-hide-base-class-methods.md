---
title: "CA1061: n&#227;o ocultar m&#233;todos de classe base | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1061: n&#227;o ocultar m&#233;todos de classe base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo derivado declara um método com o mesmo nome e com o mesmo número de parâmetros que um dos métodos de base; um ou mais dos parâmetros for um tipo de base do parâmetro correspondente no método de base; e todos os parâmetros restantes terão os tipos que são idênticos aos parâmetros correspondentes no método de base.  
  
## Descrição da Regra  
 Um método em um tipo de base é ocultado por um método idêntica nomeada em um tipo derivado quando a assinatura do parâmetro de método derivada diferem apenas pelos tipos derivados mais fraco de correspondência na assinatura do parâmetro de método de base.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remover ou renomear o método, ou alterar a assinatura do parâmetro de forma que o método não ocultar o método de base.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um método que viola a regra.  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]