---
title: "CA1049: tipos que tenham recursos nativos devem ser descart&#225;veis | Microsoft Docs"
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
  - "CA1049"
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
helpviewer_keywords: 
  - "TypesThatOwnNativeResourcesShouldBeDisposable"
  - "CA1049"
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1049: tipos que tenham recursos nativos devem ser descart&#225;veis
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|  
|CheckId|CA1049|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um tipo referencia um campo <xref:System.IntPtr?displayProperty=fullName>, um campo <xref:System.UIntPtr?displayProperty=fullName>, ou um campo <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, mas não implementa <xref:System.IDisposable?displayProperty=fullName>.  
  
## Descrição da Regra  
 Esta regra pressupõe que os campos <xref:System.IntPtr>, <xref:System.UIntPtr>, e <xref:System.Runtime.InteropServices.HandleRef> armazenam ponteiros para recursos não gerenciados.  Tipos que alocam recursos não gerenciados devem implementar <xref:System.IDisposable> para permitir que os chamadores liberem esses recursos sob demanda e reduzam o tempo de vida dos objetos que contêm os recursos.  
  
 O padrão de design recomendado para limpar recursos não gerenciados é fornecer tanto meio implícito quanto explícito para liberar esses recursos usando o método <xref:System.Object.Finalize%2A?displayProperty=fullName> e o método <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, respectivamente.  O coletor de lixo chama o método <xref:System.Object.Finalize%2A> de um objeto em algum tempo indeterminado depois que o objeto é determinado já não ser mais alcançável.  Depois que o <xref:System.Object.Finalize%2A> é chamado, uma coleta de lixo adicional é necessária para liberar o objeto.  O método <xref:System.IDisposable.Dispose%2A> permite que o chamador libere explicitamente os recursos sob demanda, antes que os recursos sejam liberados se deixados ao coletor de lixo.  Depois de limpar os recursos não gerenciados, <xref:System.IDisposable.Dispose%2A> deve chamar o método <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> para permitir que o coletor de lixo saiba que o <xref:System.Object.Finalize%2A> não mais tem que ser chamado; isso elimina a necessidade de coleta de lixo extra e diminui a vida útil do objeto.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente <xref:System.IDisposable>.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra se o tipo não referencia um recurso não gerenciado.  Caso contrário, não elimine um aviso desta regra porque a falha para implementar <xref:System.IDisposable> pode fazer com que os recursos não gerenciados se tornem indisponíveis ou subutilizados.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que implementa <xref:System.IDisposable> para limpar um recurso não gerenciado.  
  
 [!code-cs[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]  
  
## Regras Relacionadas  
 [CA2115: chamar GC.KeepAlive durante o uso de recursos nativos](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816: chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA2216: os tipos descartáveis devem declarar o finalizador](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA1001: tipos que tenham campos descartáveis devem ser descartáveis](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)  
  
## Consulte também  
 [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md)   
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)