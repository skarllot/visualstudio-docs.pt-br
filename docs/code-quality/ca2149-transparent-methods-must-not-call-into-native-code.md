---
title: "CA2149: os m&#233;todos transparentes n&#227;o devem chamar c&#243;digo nativo | Microsoft Docs"
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
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2149: os m&#233;todos transparentes n&#227;o devem chamar c&#243;digo nativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|CheckId|CA2149|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método chama uma função nativo através de um stub do método como P\/Invoke.  
  
## Descrição da Regra  
 Esta regra é acionado em qualquer método transparente que chamar diretamente em código nativo, por exemplo, com um P\/Invoke.  As violações desta regra resultam em <xref:System.MethodAccessException> na transparência de nível 2 modelo, e uma procura completa para <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> no modelo de transparência de nível 1.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o método que chama o código nativo com o atributo de <xref:System.Security.SecurityCriticalAttribute> ou de <xref:System.Security.SecuritySafeCriticalAttribute> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 [!CODE [FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode#1)]