---
title: "CA1023: os indexadores n&#227;o devem ser multidimensionais | Microsoft Docs"
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
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1023: os indexadores n&#227;o devem ser multidimensionais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|Categoria|Microsoft.Design|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um público ou um tipo protegido contêm um público ou um indicador protegido que usa mais de um índice.  
  
## Descrição da Regra  
 Os indicadores, ou seja, indexados propriedades, devem usar um único índice.  Os indicadores multidimensionais podem reduzir significativamente a usabilidade de biblioteca.  Se o design requer mais índices, reconsidere se o tipo representa um repositório de dados lógico.  Se não, use um método.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, alterar o design para usar um inteiro ou um índice solitário de cadeia de caracteres, ou usar um método em vez do medidor.  
  
## Quando Suprimir Alertas  
 Suprima um aviso desta regra somente depois cuidadosamente a consideração da necessidade do medidor não padrão.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo, `DayOfWeek03`, com um indicador multidimensional que viola a regra.  O indicador pode ser consultado como um tipo de conversão e em virtude disso é exposta mais adequadamente como um método.  O tipo é em `RedesignedDayOfWeek03` atendido para a regra.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## Regras Relacionadas  
 [CA1043: usar argumento integral ou da cadeia de caracteres para indexadores](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: usar propriedades quando apropriado](../code-quality/ca1024-use-properties-where-appropriate.md)