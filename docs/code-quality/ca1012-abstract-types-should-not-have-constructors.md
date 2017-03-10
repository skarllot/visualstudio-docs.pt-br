---
title: "CA1012: tipos abstratos n&#227;o devem ter construtores | Microsoft Docs"
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
  - "AbstractTypesShouldNotHaveConstructors"
  - "CA1012"
helpviewer_keywords: 
  - "CA1012"
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1012: tipos abstratos n&#227;o devem ter construtores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AbstractTypesShouldNotHaveConstructors|  
|CheckId|CA1012|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo público é abstrato e tem um construtor público.  
  
## Descrição da Regra  
 Construtores em tipos abstratos podem ser chamados somente por tipos derivados.  Porque construtores públicos criam instâncias de um tipo, e você não pode criar instâncias de um tipo abstrato, um tipo abstrato que tem um construtor público é criado incorretamente.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, faça o construtor protegido ou não declare o tipo como abstrato.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  O tipo abstrato tem um construtor público.  
  
## Exemplo  
 O exemplo a seguir contém um tipo abstrato que viola esta regra.  
  
 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-cs[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]  
  
## Exemplo  
 O exemplo a seguir fixa a violação anterior alterando a acessibilidade do construtor de `public` a `protected`.  
  
 [!code-cs[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]