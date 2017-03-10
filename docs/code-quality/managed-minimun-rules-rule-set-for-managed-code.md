---
title: "Conjunto de regras m&#237;nimas gerenciado para c&#243;digo gerenciado | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
caps.latest.revision: 2
caps.handback.revision: 2
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conjunto de regras m&#237;nimas gerenciado para c&#243;digo gerenciado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As regras mínimas gerenciados referem\-se aos problemas mais importantes no código, inclusive buracos na segurança em potencial, falhas de aplicativo, e outros erros importantes de lógica e de design.  Você deve incluir esta regra definida em qualquer regra personalizada e cria para seus projetos.  
  
|Regra|Descrição|  
|-----------|---------------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Tipos que possui campos descartáveis deve ser descartável|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Remova os finalizers vazias|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Os campos descartáveis devem ser removidos|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Operador de igual de sobrecarga em substituir ValueType.Equals|