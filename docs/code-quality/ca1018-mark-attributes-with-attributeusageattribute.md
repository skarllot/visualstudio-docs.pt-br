---
title: "CA1018: marcar atributos com AttributeUsageAttribute | Microsoft Docs"
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
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018: marcar atributos com AttributeUsageAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O atributo de <xref:System.AttributeUsageAttribute?displayProperty=fullName> não está presente no atributo personalizado.  
  
## Descrição da Regra  
 Quando você define um atributo personalizado, o marcará usando <xref:System.AttributeUsageAttribute> para indicar onde o código\-fonte no atributo personalizado pode ser aplicado.  O significado e o uso planejado de um atributo determinarão seus locais válidos em código.  Por exemplo, você pode definir um atributo que identifica a pessoa que é responsável por manter e aprimorar cada tipo em uma biblioteca, e que a responsabilidade sempre é atribuída ao nível do tipo.  Nesse caso, os compiladores devem habilitar o atributo em classes, enumerações, e interfaces, mas não deve habilitá\-lo em métodos, em eventos, ou propriedades.  As políticas e os procedimentos de organização ditariam se o atributo deve ser habilitado em assemblies.  
  
 A enumeração de <xref:System.AttributeTargets?displayProperty=fullName> define os destinos que você pode especificar para um atributo personalizado.  Se você omitir <xref:System.AttributeUsageAttribute>, o atributo personalizado será válida para todos os destinos, conforme definido pelo valor de `All` de enumeração de <xref:System.AttributeTargets> .  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, especifique destinos para o atributo usando <xref:System.AttributeUsageAttribute>.  Consulte o exemplo a seguir.  
  
## Quando Suprimir Alertas  
 Você deve corrigir uma violação desta regra em vez de excluir a mensagem.  Se o atributo herda <xref:System.AttributeUsageAttribute>, o atributo deve estar presente para simplificar a manutenção do código.  
  
## Exemplo  
 O exemplo a seguir define dois atributos.  `BadCodeMaintainerAttribute` omitir incorretamente a instrução de <xref:System.AttributeUsageAttribute> , e `GoodCodeMaintainerAttribute` implementa corretamente o atributo que é descrito anteriormente nesta seção.  Observe que a propriedade `DeveloperName` é exigida pela regra [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) de design e é incluída para manter a integridade.  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## Regras Relacionadas  
 [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: evitar atributos não lacrados](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Consulte também  
 [Atributos](../Topic/Attributes1.md)