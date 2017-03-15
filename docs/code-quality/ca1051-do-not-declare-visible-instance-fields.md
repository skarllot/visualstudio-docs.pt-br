---
title: "CA1051: n&#227;o declarar campos de inst&#226;ncia vis&#237;veis | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
helpviewer_keywords: 
  - "CA1051"
  - "DoNotDeclareVisibleInstanceFields"
ms.assetid: 2805376c-824c-462c-81d1-c51aaf7cabe7
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1051: n&#227;o declarar campos de inst&#226;ncia vis&#237;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVisibleInstanceFields|  
|CheckId|CA1051|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo externamente visível tem um campo externamente visível da instância.  
  
## Descrição da Regra  
 O principal uso de um campo deve ser um como detalhes de implementação.  Os campos devem ser `private` ou `internal` e devem ser exposta usando propriedades.  É tão fácil de acesso é uma propriedade como acessar um campo, e o código nos acessadores de uma propriedade pode ser alterada desde que os recursos do tipo expandem sem enviar alterações.  As propriedades que retornam apenas o valor de um campo particular ou interno são otimizadas para executar em foot de igualdade com acessar um campo; muito pequeno ganho de desempenho está associado ao uso de campos visíveis externamente sobre propriedades.  
  
 Externamente visível se refere a `public`, `protected`, e níveis de acessibilidade de `protected internal` \(`Public`, `Protected`, e `Protected Friend` no Visual Basic\).  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, faça o campo `private` ou `internal` e expõe o usando uma propriedade externamente visível.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Os campos externamente visíveis não fornece nenhum benefícios que não estão disponíveis às propriedades.  Além disso, os campos públicos não podem ser protegidos por [Demandas de link](../Topic/Link%20Demands.md).  Consulte [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Exemplo  
 O exemplo a seguir mostra um tipo \(`BadPublicInstanceFields`\) que viola esta regra.  `GoodPublicInstanceFields` mostra o código corrigido.  
  
 [!code-cs[FxCop.Design.TypesPublicInstanceFields#1](../code-quality/codesnippet/CSharp/ca1051-do-not-declare-visible-instance-fields_1.cs)]  
  
## Regras Relacionadas  
 [CA2112: os tipos seguros não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
## Consulte também  
 [Demandas de link](../Topic/Link%20Demands.md)