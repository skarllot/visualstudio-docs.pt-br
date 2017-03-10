---
title: "CA1043: usar argumento integral ou da cadeia de caracteres para indexadores | Microsoft Docs"
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
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1043: usar argumento integral ou da cadeia de caracteres para indexadores
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo protegido contêm um público ou um indicador protegido que use um tipo de índice diferente <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, ou <xref:System.String?displayProperty=fullName>.  
  
## Descrição da Regra  
 Os indicadores, ou seja, indexados propriedades, devem usar o inteiro ou em tipos para o índice.  Esses tipos são normalmente usados para indexação estruturas de dados e aumentar a usabilidade de biblioteca.  O uso do tipo de <xref:System.Object> deve ser restrito 2 os casos onde o inteiro ou o tipo específico de cadeia de caracteres não podem ser especificados em tempo de design.  Se o design requer outros tipos para o índice, reconsidere se o tipo representa um repositório de dados lógico.  Se não representa um repositório de dados lógico, use um método.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere o índice em um inteiro ou um tipo de cadeia de caracteres, ou usar um método em vez do medidor.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra somente depois cuidadosamente a consideração da necessidade do medidor não padrão.  
  
## Exemplo  
 O exemplo a seguir mostra um indicador que usa um índice de <xref:System.Int32> .  
  
 [!CODE [FxCop.Design.IntegralOrStringIndexers#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers#1)]  
  
## Regras Relacionadas  
 [CA1023: os indexadores não devem ser multidimensionais](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)