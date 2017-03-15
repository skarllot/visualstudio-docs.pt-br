---
title: "CA1714: os enums de sinalizadores devem ter nomes plurais | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714: os enums de sinalizadores devem ter nomes plurais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Uma enumeração pública tem <xref:System.FlagsAttribute?displayProperty=fullName> e seu nome não termina com “s”.  
  
## Descrição da Regra  
 Tipos que é marcado com <xref:System.FlagsAttribute> tem nomes que são plural porque o atributo indica que mais de um valor pode ser especificado.  Por exemplo, uma enumeração que define os dias da semana pode ser planejado para uso em um aplicativo onde você pode especificar vários dias.  Esta enumeração deve ter <xref:System.FlagsAttribute> e pode ser chamada “dias.  Uma enumeração semelhante que permite que somente um nível dia seja especificado não teria o atributo, e pode ser chamada “dia”.  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
## Como Corrigir Violações  
 Faça o nome da enumeração uma palavra plural, ou remover o atributo de <xref:System.FlagsAttribute> se vários valores de enumeração são especificados simultaneamente.  
  
## Quando Suprimir Alertas  
 É seguro para suprimir uma violação se o nome é uma palavra plural mas não termina com “s”.  Por exemplo, se a enumeração de vários dia que foi descrito anteriormente foi denominada “DaysOfTheWeek”, ou violaria a lógica da regra de sua mas não intencionais.  Como violações devem ser suppressd.  
  
## Regras Relacionadas  
 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Consulte também  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Design de enum](../Topic/Enum%20Design.md)