---
title: "CA1028: o armazenamento de enum deve ser Int32 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1028: o armazenamento de enum deve ser Int32
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O tipo subjacente de uma enumeração pública não é <xref:System.Int32?displayProperty=fullName>.  
  
## Descrição da Regra  
 Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas.  Por padrão, o tipo de dados de <xref:System.Int32?displayProperty=fullName> é usada para armazenar o valor constante.  Embora você possa alterar esse tipo subjacente, não é necessário ou recomendado para a maioria dos cenários.  Observe que nenhum ganho de desempenho significante é obtido usando um tipo de dados que seja menor do que <xref:System.Int32>.  Se você não pode usar o tipo de dados padrão, você deve usar um do sistema de linguagem comum \(CLS\) \- integrais tipos compatíveis, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, ou <xref:System.Int64> para garantir que todos os valores de enumeração podem ser representados em linguagens de programação compatíveis com CLS.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, a menos que os problemas de tamanho ou de compatibilidade existirem, use <xref:System.Int32>.  Em situações em que <xref:System.Int32> não é grande o suficiente para manter os valores, use <xref:System.Int64>.  Se a compatibilidade com versões anteriores requer um tipo de dados menor, use <xref:System.Byte> ou <xref:System.Int16>.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra apenas se os problemas de compatibilidade com versões anteriores a exige.  Em aplicativos, a falha e com esta regra geral não causa problemas.  Em bibliotecas, onde a interoperabilidade de idioma é necessária, a falha e com esta regra pode afetar seus usuários.  
  
## Exemplo de uma Violação  
  
### Descrição  
 O exemplo a seguir mostra duas enumerações que não usam o tipo de dados subjacente recomendado.  
  
### Código  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## Exemplo de Como Corrigir  
  
### Descrição  
 O exemplo a seguir corrige a violação anterior alterando o tipo de dados subjacente a <xref:System.Int32>.  
  
### Código  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## Regras Relacionadas  
 [CA1008: os enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: não nomeie valores de enum como 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: não use valores enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## Consulte também  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>