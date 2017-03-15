---
title: "CA1048: n&#227;o declarar membros virtuais em tipos lacrados | Microsoft Docs"
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
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1048: n&#227;o declarar membros virtuais em tipos lacrados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo utilitário for selado e declara um método que é `virtual` \(`Overridable` no Visual Basic\) e não final.  Esta regra não informa violações para os tipos de delegação, que devem seguir o padrão.  
  
## Descrição da Regra  
 Os tipos métodos declaram como virtual herdar tipos de forma que possa substituir a implementação do método virtual.  Por definição, você não pode herdar de um tipo selado, tornando um método virtual em um tipo selado sem sentido.  
  
 Os compiladores do Visual Basic.NET e C\#. não permitem que os tipos violem esta regra.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, faça o método não virtual ou fazer o tipo herdável.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Deixar o tipo em seu estado atual pode causar problemas de manutenção e não fornece nenhum benefícios.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola esta regra.  
  
 [!CODE [FxCop.Design.SealedVirtual#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual#1)]