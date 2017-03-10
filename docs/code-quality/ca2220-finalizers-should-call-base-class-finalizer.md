---
title: "CA2220: os finalizadores devem chamar o finalizador da classe base | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220: os finalizadores devem chamar o finalizador da classe base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo que substitui <xref:System.Object.Finalize%2A?displayProperty=fullName> não chama o método de <xref:System.Object.Finalize%2A> em sua classe base.  
  
## Descrição da Regra  
 O acabamento deveriam ser propagadas pela hierarquia de herança.  Para assegurar isso, os tipos devem chamar o método de <xref:System.Object.Finalize%2A> da classe base a partir de seu próprio método de <xref:System.Object.Finalize%2A> .  O compilador C\# adiciona a chamada para o finalizador da classe base automaticamente.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame o método de <xref:System.Object.Finalize%2A> do tipo base do método de <xref:System.Object.Finalize%2A> .  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  Alguns compiladores que se destinam à inserção de Common Language Runtime uma chamada para finalizador de tipo base na linguagem intermediária da Microsoft \(MSIL\).  Se um aviso dessa regra é relatado, seu compilador não insere a chamada, e você deverá adicioná\-la ao seu código.  
  
## Exemplo  
 O exemplo do Visual Basic mostra um tipo `TypeB` corretamente que chama o método de <xref:System.Object.Finalize%2A> em sua classe base.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## Consulte também  
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)