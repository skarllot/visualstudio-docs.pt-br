---
title: "CA1725: os nomes de par&#226;metro devem corresponder &#224; declara&#231;&#227;o base | Microsoft Docs"
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
  - "ParameterNamesShouldMatchBaseDeclaration"
  - "CA1725"
helpviewer_keywords: 
  - "CA1725"
  - "ParameterNamesShouldMatchBaseDeclaration"
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1725: os nomes de par&#226;metro devem corresponder &#224; declara&#231;&#227;o base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O nome de um parâmetro em uma substituição externamente visível do método não corresponde ao nome do parâmetro na instrução de base do método, o nome de parâmetro na instrução da interface do método.  
  
## Descrição da Regra  
 A nomeação consistente dos parâmetros em uma hierarquia de substituição aumentar a usabilidade das substituições do método.  Um nome de parâmetro de um método derivada que difere do nome na declaração de base pode causar confusão quanto se o método for uma substituição do método de base ou de uma nova sobrecarga do método.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, renomeie o parâmetro para corresponder à declaração de base.  A correção é uma alteração de quebra para métodos de visíveis ao.  
  
## Quando Suprimir Alertas  
 Não suprima um aviso desta regra com exceção dos métodos visíveis em bibliotecas COM que têm enviado anteriormente.