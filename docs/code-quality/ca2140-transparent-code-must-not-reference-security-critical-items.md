---
title: "CA2140: o c&#243;digo transparente n&#227;o deve fazer refer&#234;ncia a itens cr&#237;ticos de seguran&#231;a | Microsoft Docs"
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
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2140: o c&#243;digo transparente n&#227;o deve fazer refer&#234;ncia a itens cr&#237;ticos de seguran&#231;a
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método transparente:  
  
-   trata um tipo de exceção crítico da segurança  
  
-   tem um parâmetro que é marcado como um tipo crítico de segurança  
  
-   tem um parâmetro genérica com restrições críticos de uma segurança  
  
-   tem uma variável local de um tipo crítico de segurança  
  
-   faz referência a um tipo que foi marcada como a segurança crítico  
  
-   chama um método marcado como segurança crítico  
  
-   se refere a um campo que foi marcada como a segurança crítico  
  
-   retorna um tipo que foi marcada como a segurança crítico  
  
## Descrição da Regra  
 Um elemento de código que é marcado com o atributo de <xref:System.Security.SecurityCriticalAttribute> segurança é crítico.  Um método transparente não pode usar um elemento fundamental de segurança.  Se um tipo transparente tenta usar um tipo crítico de segurança <xref:System.TypeAccessException>, <xref:System.MethodAccessException> , ou <xref:System.FieldAccessException> são gerados.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, siga um destes procedimentos:  
  
-   Marcar o elemento de código que usa o código crítico de segurança com o atributo de <xref:System.Security.SecurityCriticalAttribute>  
  
     \- ou \-  
  
-   Remover o atributo de <xref:System.Security.SecurityCriticalAttribute> dos elementos de código que são marcados como segurança crítico e os marcam vez com o atributo de <xref:System.Security.SecuritySafeCriticalAttribute> ou de <xref:System.Security.SecurityTransparentAttribute> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 Nos exemplos a seguir, um método transparente tentar referenciar uma coleção genérica crítico de segurança, um campo crítico de segurança, e um método crítico de segurança.  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## Consulte também  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>