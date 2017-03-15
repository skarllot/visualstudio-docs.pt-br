---
title: "CA1406: evitar argumentos Int64 para clientes do Visual Basic 6 | Microsoft Docs"
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
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
helpviewer_keywords: 
  - "AvoidInt64ArgumentsForVB6Clients"
  - "CA1406"
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1406: evitar argumentos Int64 para clientes do Visual Basic 6
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidInt64ArgumentsForVB6Clients|  
|CheckId|CA1406|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo que é marcado como especificamente visível ao Component Object Model \(COM\) declara um membro que usa um argumento de <xref:System.Int64?displayProperty=fullName> .  
  
## Descrição da Regra  
 Os clientes do Visual Basic 6 COM não podem acessar inteiros de 64 bits.  
  
 Por padrão, os seguintes são visíveis à: os assemblies, tipos de chaves pública, membros públicos da instância do no utilitário, e todos os membros de tipos de valor públicos.  No entanto, para reduzir falsos positivos, essa regra requer a visibilidade de COM o tipo ser declarado explicitamente; o assembly contentor deve ser marcado com <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false` e o tipo deve ser marcado com <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra para um parâmetro cujo valor sempre possa ser expresso como uma integrante de 32 bits, altere o tipo de parâmetro a <xref:System.Int32?displayProperty=fullName>.  Se o valor de parâmetro pode ser maior que pode ser expresso como uma integrante de 32 bits, altere o tipo de parâmetro a <xref:System.Decimal?displayProperty=fullName>.  Observe que <xref:System.Single?displayProperty=fullName> e <xref:System.Double?displayProperty=fullName> perdem a precisão em intervalos principais do tipo de dados de <xref:System.Int64> .  Se o membro não deve ser visível para o, o marcará com <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `false`.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se você tiver certeza de que os clientes do Visual Basic 6 COM não acessarão o tipo.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-cs[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]  
  
## Regras Relacionadas  
 [CA1413: evitar campos não públicos em tipos de valor visíveis COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: evitar membros estáticos em tipos visíveis COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Consulte também  
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Tipo de dados Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)