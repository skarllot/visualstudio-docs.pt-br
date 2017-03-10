---
title: "CA2142: o c&#243;digo transparente n&#227;o deve ser protegido com LinkDemands | Microsoft Docs"
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
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2142: o c&#243;digo transparente n&#227;o deve ser protegido com LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método transparente requer <xref:System.Security.Permissions.SecurityAction> ou outra procura de segurança.  
  
## Descrição da Regra  
 Esta regra é disparada os métodos que exigem LinkDemands transparentes para acessá\-los.  A segurança que o código transparente não deve ser responsável para verificar a segurança de uma operação, e não deve solicitar permissões em virtude disso.  Como os métodos são transparentes suponha para ser neutro de segurança, não devem fazer nenhuma decisões de segurança.  Além disso, o código crítico de seguro, que tomar decisões de segurança, não deve confiar no código transparente para ter feito anteriormente essa decisão.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, para remover a procura de link no método ou transparente para marcar o método com o atributo de <xref:System.Security.SecuritySafeCriticalAttribute> se estiver executando verificações de segurança, como a segurança requer.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 No exemplo a seguir, a regra é acionado no método como o método é transparente e é marcado com um LinkDemand <xref:System.Security.PermissionSet> que contém <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Não elimine um alerta desta regra.