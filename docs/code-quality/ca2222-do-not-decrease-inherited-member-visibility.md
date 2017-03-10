---
title: "CA2222: n&#227;o diminuir a visibilidade de membro herdada | Microsoft Docs"
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
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2222: n&#227;o diminuir a visibilidade de membro herdada
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um método particular em um tipo não selado tem uma assinatura idêntica a um método público declarado em um tipo base.  O método particular não é final.  
  
## Descrição da Regra  
 Você não deve alterar o modificador de acesso para membros herdados.  Alterar um membro herdado para particular não impede que os chamadores acessem a implementação da classe base do método.  Se o membro for tornado particular e o tipo for não lacrado, tipos herdeiros podem chamar a implementação pública mais recente do método na hierarquia de herança.  Se você precisar modificar o modificador de acesso, ou o método deve ser marcado como final ou seu tipo deve ser selado para impedir que o método seja substituído.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o acesso para ser não\-particular.  Como alternativa, se sua linguagem de programação o permitir, você tornar o método final.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola esta regra.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]