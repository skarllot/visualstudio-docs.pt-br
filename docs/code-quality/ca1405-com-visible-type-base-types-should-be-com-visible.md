---
title: "CA1405: os tipos base de tipo vis&#237;vel em COM devem ser vis&#237;veis em COM | Microsoft Docs"
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
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405: os tipos base de tipo vis&#237;vel em COM devem ser vis&#237;veis em COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|DependsOnFix|  
  
## Causa  
 Um tipo visível do Component Object Model \(COM\) é derivado de um tipo que não é visível COM.  
  
## Descrição da Regra  
 Quando um tipo de visível COM adiciona membros em uma nova versão, deve habitar por diretrizes restringidas para evitar dividir os clientes COM que são associados à versão atual.  Um tipo que é invisível a COM presume que não precisará seguir estas regras de controle de versão do COM quando adiciona novos membros.  No entanto, se um tipo de visível COM se deriva do tipo invisível COM e se expõe uma interface da classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou de <xref:System.Runtime.InteropServices.ClassInterfaceType> \(o padrão\), todos os membros públicos do tipo de base \(a menos que são marcados como invisível COM especificamente, que seriam redundantes\) são expostos COM.  Se o tipo de base adiciona novos membros em uma versão subsequente, todos os clientes COM que se associarem à interface da classe de tipo derivado podem interromper.  Os tipos de devem derivar COM visíveis apenas os tipos visíveis COM para reduzir a possibilidade de interromper clientes COM.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, torne os tipos de base COM visível ou invisível COM o tipo derivado.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## Consulte também  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/pt-br/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)