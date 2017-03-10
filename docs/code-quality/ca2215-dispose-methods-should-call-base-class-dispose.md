---
title: "CA2215: os m&#233;todos de descarte devem chamar o descarte da classe base | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215: os m&#233;todos de descarte devem chamar o descarte da classe base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> herda de um tipo que também implementa <xref:System.IDisposable>.  O método de <xref:System.IDisposable.Dispose%2A> do tipo herdando não chama o método de <xref:System.IDisposable.Dispose%2A> do tipo pai.  
  
## Descrição da Regra  
 Se um tipo é herdada de um tipo descartável, deve chamar o método de <xref:System.IDisposable.Dispose%2A> do tipo de base de dentro de seu próprio método de <xref:System.IDisposable.Dispose%2A> .  Chamando o método do tipo de base descartado garante que todos os recursos criados pelo tipo de base sejam liberados.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame `base`.<xref:System.IDisposable.Dispose%2A> em seu método de <xref:System.IDisposable.Dispose%2A> .  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se a chamada a `base`.<xref:System.IDisposable.Dispose%2A> ocorre no nível mais profundo de chamada das verificações de regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo `TypeA` que implementa <xref:System.IDisposable>.  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## Exemplo  
 O exemplo a seguir mostra um tipo `TypeB` que herda do tipo `TypeA` corretamente e chama seu método de <xref:System.IDisposable.Dispose%2A> .  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_1.vb)]  
  
## Consulte também  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)