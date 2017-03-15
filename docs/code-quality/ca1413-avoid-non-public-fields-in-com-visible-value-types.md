---
title: "CA1413: evitar campos n&#227;o p&#250;blicos em tipos de valor vis&#237;veis COM | Microsoft Docs"
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
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413: evitar campos n&#227;o p&#250;blicos em tipos de valor vis&#237;veis COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|Categoria|Microsoft.Interoperability|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um tipo de valor marcado como especificamente visível ao Component Object Model \(COM\) declara um campo público da instância.  
  
## Descrição da Regra  
 Os campos público da instância de tipo de valor COM\- visíveis são visíveis aos clientes COM.  Revise o conteúdo do campo para informações que não são expostos, ou que terá um design ou um efeito não intencional de segurança.  
  
 Por padrão, todos os tipos de valores de chaves pública são visíveis na.  No entanto, para reduzir falsos positivos, essa regra requer a visibilidade de COM o tipo ser declarado explicitamente.  O assembly contentor deve ser marcado com <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false` e o tipo deve ser marcado com <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra e manter o campo oculto, altere o tipo de valor em um tipo de referência ou remover o atributo de <xref:System.Runtime.InteropServices.ComVisibleAttribute> do tipo.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se a exposição pública do campo for aceitável.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo que viola a regra.  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## Regras Relacionadas  
 [CA1407: evitar membros estáticos em tipos visíveis COM](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Consulte também  
 [Interoperação com código não gerenciado](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualificando tipos do .NET para interoperação](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)