---
title: "CA1809: evitar locais excessivos | Microsoft Docs"
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
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1809: evitar locais excessivos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Categoria|Microsoft.Performance|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um membro contém mais de 64 variáveis locais, alguns dos quais pode ser gerado completo.  
  
## Descrição da Regra  
 Uma otimização comuns de desempenho é armazenar um valor em um registro de processador em vez de na memória, que é referenciada como *enregistering* o valor.  Common Language Runtime consulte até 64 variáveis locais para o enregistration.  As variáveis que não enregistered são colocados na pilha e devem ser movidos para um registro antes da manipulação.  Para permitir a chance de que todas as variáveis locais obtém enregistered, limita o número de variáveis locais a 64.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, refactor a implementação para não usar mais de 64 variáveis locais.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso desta regra, ou desabilitar a regra, se o desempenho não é um problema.  
  
## Regras Relacionadas  
 [CA1804: remover locais não usados](../code-quality/ca1804-remove-unused-locals.md)