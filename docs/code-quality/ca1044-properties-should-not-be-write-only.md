---
title: "CA1044: as propriedades n&#227;o devem ser somente leitura | Microsoft Docs"
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
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1044: as propriedades n&#227;o devem ser somente leitura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O utilitário ou a propriedade protegida têm um acessador set mas não têm um acessador obtidos.  
  
## Descrição da Regra  
 Obter acessadores fornecem acesso de leitura a uma propriedade e os acessadores ajustados fornecem acesso de gravação.  Embora seja aceitável e geralmente necessário ter uma propriedade somente leitura, as diretrizes de design proíbem o uso de propriedades somente gravação.  Isso é porque permitindo que um usuário defina um valor e depois impedir que o usuário exibe o valor não fornece nenhuma segurança.  Além disso, sem acesso de leitura, o estado de objetos compartilhados não pode ser exibido, o que limita sua utilidade.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, adicione um acessador obter à propriedade.  Como alternativa, se o comportamento de uma propriedade somente leitura é necessário, considere converta essa propriedade para um método.  
  
## Quando Suprimir Alertas  
 É altamente recomendável que você não suprime um aviso desta regra.  
  
## Exemplo  
 No exemplo a seguir, `BadClassWithWriteOnlyProperty` é um tipo com uma propriedade somente leitura.  `GoodClassWithReadWriteProperty` contém o código corrigido.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]