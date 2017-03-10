---
title: "CA1501: evitar heran&#231;a excessiva | Microsoft Docs"
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
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1501: evitar heran&#231;a excessiva
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Categoria|Microsoft.Maintainability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo é mais de quatro níveis abaixo na hierarquia de herança.  
  
## Descrição da Regra  
 As hierarquias profundamente aninhadas de classificação podem ser difíceis de seguida, compreendam, e manter.  Essa análise de limites de regra hierarquias no mesmo módulo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, derivar o tipo de um tipo de base que seja menor profundo na hierarquia de herança ou eliminar qualquer um dos tipos de base intermediários.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra.  Porém, o código pode ser mais difícil de manter.  Observe que, como a visibilidade dos tipos de base, resolvendo violações desta regra pode criar alterações.  Por exemplo, remova os tipos de base públicos é uma alteração.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]