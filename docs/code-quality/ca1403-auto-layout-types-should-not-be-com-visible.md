---
title: "CA1403: os tipos de layout autom&#225;tico n&#227;o devem ser vis&#237;veis em COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403: os tipos de layout autom&#225;tico n&#227;o devem ser vis&#237;veis em COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo de valor visível do Component Object Model \(COM\) é marcado com o atributo de <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> definido como <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## Descrição da Regra  
 os tipos de layout de<xref:System.Runtime.InteropServices.LayoutKind> são gerenciados por Common Language Runtime.  O layout deless podem ser alterados entre versões do.NET Framework, que interromperão clientes COM que esperam por um layout específico.  Observe que se o atributo de <xref:System.Runtime.InteropServices.StructLayoutAttribute> não for especificado, o C\#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], e os compiladores C\+\+ especificam o layout de <xref:System.Runtime.InteropServices.LayoutKind> para tipos de valor.  
  
 A menos que marcados de outra forma, todos os tipos públicos não são visíveis à; todos os tipos genéricos público e são invisíveis COM.  No entanto, para reduzir falsos positivos, essa regra requer a visibilidade de COM o tipo ser declarado explicitamente; o assembly contentor deve ser marcado com <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false` e o tipo deve ser marcado com <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o valor do atributo de <xref:System.Runtime.InteropServices.StructLayoutAttribute> a <xref:System.Runtime.InteropServices.LayoutKind> ou a <xref:System.Runtime.InteropServices.LayoutKind>, ou fazer o tipo invisível COM.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra e um tipo que satisfaça a regra.  
  
 [!CODE [FxCop.Interoperability.AutoLayout#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout#1)]  
  
## Regras Relacionadas  
 [CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Consulte também  
 [Introducing the Class Interface](http://msdn.microsoft.com/pt-br/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualificando tipos do .NET para interoperação](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)