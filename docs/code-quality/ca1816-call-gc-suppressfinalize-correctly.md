---
title: "CA1816: chamar GC.SuppressFinalize corretamente | Microsoft Docs"
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
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
helpviewer_keywords: 
  - "CA1816"
  - "DisposeMethodsShouldCallSuppressFinalize"
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1816: chamar GC.SuppressFinalize corretamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGCSuppressFinalizeCorrectly|  
|CheckId|CA1816|  
|Categoria|Microsoft.  Uso|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
  
-   Um método que é uma implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> não chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Um método que não é uma implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
-   Chama um método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> e passa algo diferente do \(i no Visual Basic\).  
  
## Descrição da Regra  
 O método de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> permite que os usuários liberar a qualquer momento recursos antes do objeto que fica disponível para coleta de lixo.  Se o método de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> é chamado, libera recursos do objeto.  Isso torna o acabamento desnecessário.  <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> deve chamar <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> assim que o coletor de lixo não chama o finalizador do objeto.  
  
 Para evitar tipos derivados com os finalizers do têm que implementam novamente [System.IDisposable](assetId:///System.IDisposable?qualifyHint=True&autoUpgrade=False) e chamar, tipos unsealed sem finalizers ainda deve chamar <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
## Como Corrigir Violações  
 Para corrigir uma violação dessa regra:  
  
 Se o método for uma implementação de <xref:System.IDisposable.Dispose%2A>, adicione uma chamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  
  
 Se o método não é uma implementação de <xref:System.IDisposable.Dispose%2A>, ou remover a chamada a <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> ou movê\-lo para a implementação de <xref:System.IDisposable.Dispose%2A> do tipo.  
  
 Alterar qualquer chamada para<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para transmitir isso a \(no Visual Basic\).  
  
## Quando Suprimir Alertas  
 Suprima apenas um aviso dessa regra se você estiver usando deliberando <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para controlar o tempo de vida de outros objetos.  Não suprima um aviso dessa regra se uma implementação de <xref:System.IDisposable.Dispose%2A> não chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>.  Nessa situação, não suprime o acabamento prejudica o desempenho e não fornece nenhum benefício.  
  
## Exemplo  
 O exemplo a seguir mostra um método que chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>incorretamente.  
  
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/VisualBasic/ca1816-call-gc-suppressfinalize-correctly_1.vb)]
 [!code-cs[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../code-quality/codesnippet/CSharp/ca1816-call-gc-suppressfinalize-correctly_1.cs)]  
  
## Exemplo  
 O exemplo a seguir mostra um método que chama <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>corretamente.  
  
 [!CODE [FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1)]  
  
## Regras Relacionadas  
 [CA2215: os métodos de descarte devem chamar o descarte da classe base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
## Consulte também  
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)