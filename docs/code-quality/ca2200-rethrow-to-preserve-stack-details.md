---
title: "CA2200: relan&#231;ar para preservar detalhes da pilha | Microsoft Docs"
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
  - "RethrowToPreserveStackDetails"
  - "CA2200"
helpviewer_keywords: 
  - "CA2200"
  - "RethrowToPreserveStackDetails"
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2200: relan&#231;ar para preservar detalhes da pilha
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RethrowToPreserveStackDetails|  
|CheckId|CA2200|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Uma exceção é lançada novamente e a exceção é especificada explicitamente na declaração `throw`.  
  
## Descrição da Regra  
 Uma vez que uma exceção é gerada, a parte das informações que ela contém está no rastreamento de pilha.  O rastreamento de pilha é uma lista da hierarquia de chamada de método que começa com o método que gera a exceção e termina com o método que captura a exceção.  Se uma exceção for gerada novamente pela especificação da exceção na declaração `throw`, o rastreamento de pilha será reiniciado no método atual e a lista de chamadas de métodos entre o método original que apresentou a exceção e o método atual será perdida.  Para manter as informações originais do rastreamento de pilha com a exceção, use a declaração `throw` sem especificar a exceção.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, gere novamente a exceção sem especificar a exceção explicitamente.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  
  
## Exemplo  
 O exemplo a seguir mostra um método, `CatchAndRethrowExplicitly`, que viola a regra e um método, `CatchAndRethrowImplicitly`, que satisfaz a regra.  
  
 [!CODE [FxCop.Usage.Rethrow#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.Rethrow#1)]