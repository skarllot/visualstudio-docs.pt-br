---
title: "CA2213: os campos descart&#225;veis devem ser descartados | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213: os campos descart&#225;veis devem ser descartados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName> declara os campos que são de tipos que também implementam <xref:System.IDisposable>.  O método de <xref:System.IDisposable.Dispose%2A> do campo não é chamado pelo método de <xref:System.IDisposable.Dispose%2A> do tipo declarando.  
  
## Descrição da Regra  
 Um tipo é responsável para descartar de todos os recursos não gerenciados; isso é feito implementando <xref:System.IDisposable>.  Esta regra verifica se um tipo descartável `T` declara um campo `F` que é uma instância de um tipo descartável `FT`.  Para cada campo `F`, a regra tenta localizar uma chamada a `FT.Dispose`.  A regra pesquisa os métodos chamados por `T.Dispose`, e um mais nível inferior \(os métodos chamados pelos métodos chamados por `FT.Dispose`\).  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, chame <xref:System.IDisposable.Dispose%2A> nos campos que são de tipos que implementam <xref:System.IDisposable> se você é responsável para alocar e libere os recursos não gerenciados mantidos pelo campo.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se você não é responsável para liberar o recurso ocupado pelo campo, ou se a chamada a <xref:System.IDisposable.Dispose%2A> ocorre no nível mais profundo de chamada do que a regra verifica.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo `TypeA` que implementa <xref:System.IDisposable> \(`FT` na discussão de previosu\).  
  
 [!CODE [FxCop.Usage.IDisposablePattern#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposablePattern#1)]  
  
## Exemplo  
 O exemplo a seguir mostra um tipo `TypeB` que viola esta regra declarando um campo `aFieldOfADisposableType` \(`F` na discussão anterior\) como um tipo descartável \(`TypeA`\) e não chamando <xref:System.IDisposable.Dispose%2A> no campo.  `TypeB` corresponde a `T` na discussão anterior.  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## Consulte também  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)