---
title: "CA2216: os tipos descart&#225;veis devem declarar o finalizador | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216: os tipos descart&#225;veis devem declarar o finalizador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo que implementa <xref:System.IDisposable?displayProperty=fullName>, e tem os campos que sugerem o uso de recursos não gerenciados, não implementa um finalizer como descrito por <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
## Descrição da Regra  
 Uma violação dessa regra é relatada se o tipo descartável contém campos dos seguintes tipos:  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente um finalizer que chama o seu método <xref:System.IDisposable.Dispose%2A>.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra se o tipo não implementa <xref:System.IDisposable> com o objetivo de liberar recursos não gerenciados.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola esta regra.  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## Regras Relacionadas  
 [CA2115: chamar GC.KeepAlive durante o uso de recursos nativos](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)  
  
 [CA1816: chamar GC.SuppressFinalize corretamente](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: tipos que tenham recursos nativos devem ser descartáveis](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## Consulte também  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Padrão de descarte](../Topic/Dispose%20Pattern.md)