---
title: "CA1034: os tipos aninhados n&#227;o devem ser vis&#237;veis | Microsoft Docs"
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
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1034: os tipos aninhados n&#227;o devem ser vis&#237;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo externamente visível contém uma declaração de tipo externamente visível.  As enumerações aninhadas e os tipos protegidos são isentos desta regra.  
  
## Descrição da Regra  
 Um tipo aninhado é um tipo declarado no escopo de outro tipo.  Os tipos aninhados são úteis para encapsular detalhes de implementação privados do tipo contentor.  Usados para essa finalidade, os tipos aninhados não devem ser externamente visíveis.  
  
 Não use tipos aninhados externamente visíveis para o agrupamento lógico ou não para evitar colisões de nome; em vez disso, use namespaces.  
  
 Os tipos aninhados incluem a noção de acessibilidade do membro, que alguns programadores não entendem claramente.  
  
 Os tipos protegidos podem ser usados nas subclasses e aninhados em cenários de personalização dos tipos com antecedência.  
  
## Como Corrigir Violações  
 Se você não pretende o tipo ser aninhado externamente visível, altere a acessibilidade do tipo.  Se não, remova o tipo aninhado de seu pai.  Se a finalidade de aninhamento é categorizar o tipo aninhado, use um namespace para criar em vez da hierarquia.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]