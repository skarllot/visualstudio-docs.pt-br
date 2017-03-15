---
title: "CA2141:Transparent m&#233;todos n&#227;o devem atender a LinkDemands | Microsoft Docs"
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
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2141:Transparent m&#233;todos n&#227;o devem atender a LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método transparente de segurança chama um método em um assembly que não é marcado com o atributo de <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\), ou um método transparente de segurança satisfaz <xref:System.Security.Permissions.SecurityAction>`.LinkDemand` para um tipo ou um método.  
  
## Descrição da Regra  
 Atender a um LinkDemand é uma operação confidencial de segurança que pode causar a elevação não intencional de privilégios.  O código transparente de segurança não deve atender a LinkDemands, porque não está sujeito aos mesmos requisitos de auditoria de segurança que o código crítico de segurança.  Os métodos transparentes em assemblies definidos de nível 1 da regra de segurança causarão qualquer LinkDemands que satisfazem para ser convertidos em tempo de execução para as demandas completas, que podem causar problemas de desempenho.  Em assemblies definidos de nível 2 da regra de segurança, os métodos transparentes não serão mais no compilador de \(JIT\) just\-in\-time se tentarem atender a um LinkDemand.  
  
 Em assemblies que a segurança de nível 2 do usee, o tentará por um método transparente de segurança de atender a um LinkDemand ou de chamar um método em um assembly de non\-APTCA aumenta <xref:System.MethodAccessException>; nos assemblies de nível 1 é o LinkDemand se torna uma procura completa.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, marque o método acessando com o atributo de <xref:System.Security.SecurityCriticalAttribute> ou de <xref:System.Security.SecuritySafeCriticalAttribute> , ou remover o LinkDemand do método acessado.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 Neste exemplo, um método transparente tentar chamar um método que tem um LinkDemand.  Esta regra será acionado neste código.  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]