---
title: "CA1814: preferir matrizes denteadas em rela&#231;&#227;o &#224;s multidimensionais | Microsoft Docs"
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
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1814: preferir matrizes denteadas em rela&#231;&#227;o &#224;s multidimensionais
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um membro é declarado como uma matriz multidimensional.  
  
## Descrição da Regra  
 Uma matriz denteada é uma matriz cujos elementos sejam matrizes.  As matrizes que compõem os elementos podem ser de tamanhos diferentes, o que leva ao menos espaço desperdiçado para alguns conjuntos de dados.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, altere a matriz multidimensional em uma matriz denteada.  
  
## Quando Suprimir Alertas  
 Suprima um aviso dessa regra se a matriz multidimensional não perde espaço.  
  
## Exemplo  
 O exemplo a seguir mostra declarações para irregular e matrizes multidimensionais.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]