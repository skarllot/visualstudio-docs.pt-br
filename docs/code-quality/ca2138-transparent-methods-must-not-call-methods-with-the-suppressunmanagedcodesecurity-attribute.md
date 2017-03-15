---
title: "CA2138: os m&#233;todos transparentes n&#227;o devem chamar m&#233;todos com o atributo SuppressUnmanagedCodeSecurity | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138: os m&#233;todos transparentes n&#227;o devem chamar m&#233;todos com o atributo SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método transparente de segurança chama um método marcado com o atributo de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> .  
  
## Descrição da Regra  
 Esta regra é acionado em qualquer método transparente que chamar diretamente em código nativo, por exemplo, usando a através de uma chamada de invocação de plataforma \(P\/Invoke\).  Métodos de interoperabilidade de P\/Invoke e de COM que são marcados com o resultado do atributo de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> em um LinkDemand que está sendo feita no método de chamada.  Como o código transparente de segurança não pode atender LinkDemands, o código também não pode chamar os métodos que são marcados com o atributo de SuppressUnmanagedCodeSecurity, ou os métodos da classe que é marcada com atributo de SuppressUnmanagedCodeSecurity.  Haverá falha no método, ou a demanda será convertida em uma procura completa.  
  
 As violações desta regra resultam em <xref:System.MethodAccessException> no modelo de transparência da segurança de nível 2, e uma procura completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> no modelo de transparência de nível 1.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, remova o atributo de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> e marcar o método com <xref:System.Security.SecurityCriticalAttribute> ou atributo de <xref:System.Security.SecuritySafeCriticalAttribute> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]