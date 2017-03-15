---
title: "CA1802: usar literais quando apropriado | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
helpviewer_keywords: 
  - "UseLiteralsWhereAppropriate"
  - "CA1802"
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1802: usar literais quando apropriado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseLiteralsWhereAppropriate|  
|CheckId|CA1802|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um campo é declarado `static` e `readonly` \(`Shared` e `ReadOnly` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), e iniciado com um valor que é computável em tempo de compilação.  
  
## Descrição da Regra  
 O valor de um campo de `static``readonly` é computado pelo tempo de execução quando o construtor estático para o tipo declarando é chamado.  Se o campo de `static``readonly` é inicializado quando é declarado e um construtor estático não é declarada explicitamente, o compilador emite um construtor estático para inicializar o campo.  
  
 O valor de um campo de `const` é computado em tempo de compilação e armazenado nos metadados, que aumenta o desempenho de tempo de execução quando comparado a um campo de `static``readonly` .  
  
 Como o valor atribuído ao campo de destino é computável em tempo de compilação, altere a declaração para um campo de `const` de forma que o valor é computado em tempo de compilação em vez de em tempo de execução.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, substitua os modificadores de `static` e de `readonly` com o modificador de `const` .  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra, ou desabilitar a regra, se o desempenho não é interessante.  
  
## Exemplo  
 O exemplo a seguir mostra um tipo, `UseReadOnly`, que viola a regra e um tipo, `UseConstant`, que obedece à regra.  
  
 [!CODE [FxCop.Performance.UseLiterals#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals#1)]