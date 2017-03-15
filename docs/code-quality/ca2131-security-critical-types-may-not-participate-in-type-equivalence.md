---
title: "CA2131: os tipos cr&#237;ticos de seguran&#231;a podem n&#227;o participar da equival&#234;ncia de tipo | Microsoft Docs"
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
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131: os tipos cr&#237;ticos de seguran&#231;a podem n&#227;o participar da equival&#234;ncia de tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo participa da equivalência do tipo e o próprio tipo, ou um membro ou campo de tipo, é marcado com o atributo de <xref:System.Security.SecurityCriticalAttribute> .  
  
## Descrição da Regra  
 Esta regra é acionado em qualquer tipo críticos ou em tipos que contenha os métodos importantes ou os campos que estão participando da equivalência do tipo.  Quando CLR detecta essa tipo, não o carrega com <xref:System.TypeLoadException> em tempo de execução.  Normalmente, esta regra ser disparado apenas quando equivalência do tipo de ferramentas dos usuários manualmente em vez de confiar em tlbimp e os compiladores para fazer a equivalência do tipo.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o atributo de SecurityCritical.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 Os exemplos a seguir demonstram uma interface, um método, e um campo que provocou essa regra seja acionado.  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## Consulte também  
 [Código transparente de segurança, nível 2](../Topic/Security-Transparent%20Code,%20Level%202.md)