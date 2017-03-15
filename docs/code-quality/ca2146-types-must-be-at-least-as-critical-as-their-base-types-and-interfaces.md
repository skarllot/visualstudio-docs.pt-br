---
title: "CA2146: tipos devem ser pelo menos cr&#237;ticos como tipos base e interfaces | Microsoft Docs"
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
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2146: tipos devem ser pelo menos cr&#237;ticos como tipos base e interfaces
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo transparente é derivado de um tipo que é marcado com <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityCriticalAttribute>, ou um tipo que é marcado com o atributo de <xref:System.Security.SecuritySafeCriticalAttribute> é derivado de um tipo que é marcado com o atributo de <xref:System.Security.SecurityCriticalAttribute> .  
  
## Descrição da Regra  
 Esta regra é disparada quando um tipo derivado tem um atributo de transparência de segurança que não seja tão importante quanto sua tipo de base ou interface implementada.  Apenas os tipos críticos podem derivar os tipos de base críticos ou implementar interfaces críticos do, e apenas os tipos críticos ou seguro\- críticos podem derivar os tipos de base seguro\- críticos ou implementar interfaces seguro\- críticos.  Violações desta regra no resultado da transparência de nível 2 em <xref:System.TypeLoadException> para o tipo derivado.  
  
## Como Corrigir Violações  
 Para corrigir essa violação, marque o tipo derivado ou implementando com um atributo de transparência pelo menos que seja tão importante quanto o tipo de base ou a interface.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 [!CODE [FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes#1)]