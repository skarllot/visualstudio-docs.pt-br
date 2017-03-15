---
title: "CA2145: os m&#233;todos transparentes n&#227;o devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145: os m&#233;todos transparentes n&#227;o devem ser decorados com o SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método transparente, um método marcado com o método de <xref:System.Security.SecuritySafeCriticalAttribute> , ou um tipo que contém um método são marcados com o atributo de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> .  
  
## Descrição da Regra  
 Os métodos decorados com o atributo de <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> têm um LinkDemand implícito colocado em cima de qualquer método que chama.  Este LinkDemand requer que o código de chamada é segurança crítico.  Marcar o método que usa SuppressUnmanagedCodeSecurity com o atributo de <xref:System.Security.SecurityCriticalAttribute> faz esse requisito mais óbvio para chamadores do método.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o método ou o tipo com o atributo de <xref:System.Security.SecurityCriticalAttribute> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
### Código  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### Comentários