---
title: "CA1011: considere a passagem dos tipos base como par&#226;metros | Microsoft Docs"
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
  - "ConsiderPassingBaseTypesAsParameters"
  - "CA1011"
helpviewer_keywords: 
  - "CA1011"
  - "ConsiderPassingBaseTypesAsParameters"
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1011: considere a passagem dos tipos base como par&#226;metros
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConsiderPassingBaseTypesAsParameters|  
|CheckId|CA1011|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Uma declaração do método inclui um parâmetro formal que é um tipo derivado, e o método chama somente membros de tipo base do parâmetro.  
  
## Descrição da Regra  
 Quando um tipo de base é especificado como um parâmetro em uma declaração do método, qualquer tipo derivado do tipo de base pode ser passado como o argumento correspondente ao método.  Quando o argumento é usado no corpo do método, o método específico executado dependerá do tipo de argumento.  Se a funcionalidade extra fornecida por tipo derivado não for necessária, o uso do tipo de base permite um uso mais amplo do método.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o tipo do parâmetro ao seu tipo base.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra  
  
-   se o método requer a funcionalidade específica que é fornecida por derivada digite  
  
     \- ou \-  
  
-   para impor que somente o tipo derivado, ou um tipo mais derivada, são passados para o método.  
  
 Nesses casos, o código será mais robusto devido à verificação de tipo forte que é fornecida no compilador e o tempo de execução.  
  
## Exemplo  
 O exemplo a seguir mostra um método, `ManipulateFileStream`, que pode ser usado somente com um objeto de <xref:System.IO.FileStream> , que viola esta regra.  Um segundo método, `ManipulateAnyStream`, obedece à regra substituindo o parâmetro de <xref:System.IO.FileStream> usando <xref:System.IO.Stream>.  
  
 [!code-cs[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]  
  
## Regras Relacionadas  
 [CA1059: os membros não devem expor determinados tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)