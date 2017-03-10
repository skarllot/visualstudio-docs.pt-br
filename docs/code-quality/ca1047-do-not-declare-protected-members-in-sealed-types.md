---
title: "CA1047: n&#227;o declarar membros protegidos em tipos lacrados | Microsoft Docs"
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
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1047: n&#227;o declarar membros protegidos em tipos lacrados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo utilitário for `sealed` \(`NotInheritable` no Visual Basic\) e declara um membro protegido ou um tipo aninhado protegido.  Esta regra não informa violações dos métodos de <xref:System.Object.Finalize%2A> , que devem seguir o padrão.  
  
## Descrição da Regra  
 Os tipos declaram membros protegidos herdar tipos de forma que possa acessar ou substituir o membro.  Por definição, você não pode herdar de um tipo selado, o que significa que os métodos protegidos em tipos selados não podem ser chamados.  
  
 O compilador C\# emite um aviso para esse erro.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o nível de acesso de membro em particular, ou fazer o tipo herdável.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Deixar o tipo em seu estado atual pode causar problemas de manutenção e não fornece nenhum benefícios.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola esta regra.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]