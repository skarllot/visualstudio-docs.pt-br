---
title: "CA1059: os membros n&#227;o devem expor determinados tipos concretos | Microsoft Docs"
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
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
helpviewer_keywords: 
  - "CA1059"
  - "MembersShouldNotExposeCertainConcreteTypes"
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1059: os membros n&#227;o devem expor determinados tipos concretos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MembersShouldNotExposeCertainConcreteTypes|  
|CheckId|CA1059|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um membro externamente visível é qualquer tipo concreto ou expõe certos tipos concretos com um de seus parâmetros ou valor de retorno.  Atualmente, esta regra relata a exposição dos seguintes tipos: concretos  
  
-   Um tipo derivado de <xref:System.Xml.XmlNode?displayProperty=fullName>.  
  
## Descrição da Regra  
 Um tipo concreto é um tipo que tenha uma implementação completo e em virtude disso pode ser criada uma instância.  Para permitir uso completo do membro, substitua o tipo concreto com a interface sugerida.  Isso permite que o membro aceita qualquer tipo que implemente a interface ou é usado onde um tipo que implementa a interface é esperado.  
  
 A tabela a seguir lista os tipos concretos de destino e as substituições sugeridas.  
  
|Tipo concreto|Substituição|  
|-------------------|------------------|  
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> Usando a interface desacopla o membro de uma implementação específica de uma fonte de dados XML.|  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o tipo concreto à interface sugerida.  
  
## Quando Suprimir Alertas  
 É seguro para suprimir uma mensagem dessa regra se a funcionalidade específica fornecida pelo tipo concreto é necessária.  
  
## Regras Relacionadas  
 [CA1011: considere a passagem dos tipos base como parâmetros](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)