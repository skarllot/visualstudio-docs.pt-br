---
title: "CA2226: os operadores devem ter sobrecargas sim&#233;tricas | Microsoft Docs"
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
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2226: os operadores devem ter sobrecargas sim&#233;tricas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|Categoria|Microsoft.Usage|  
|Alteração Significativa|Sem Quebra|  
  
## Causa  
 Um tipo implementa o operador de igualdade ou de desigualdade e não implementa o operador oposto.  
  
## Descrição da Regra  
 Não há nenhuma circunstância onde a igualdade ou desigualdade é aplicável às instâncias de um tipo, e o operador oposto é indefinido.  Os tipos implementam normalmente o operador de desigualdade retornar o valor negativo do operador de igualdade.  
  
 O compilador C\# emite um erro para violações desta regra.  
  
## Como Corrigir Violações  
 Para corrigir uma violação desta regra, implemente os operadores de igualdade e de desigualdade, ou remover o que estiver presente.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.  O tipo não funcionará de um modo que é consistente com [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Regras Relacionadas  
 [CA1046: não sobrecarregar igualdades de operador em tipos de referência](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: as sobrecargas do operador têm alternativas nomeadas](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)  
  
 [CA2224: substituir igualdades em igualdades de operador de sobrecarga](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: substituir GetHashCode em igualdades de substituição](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: sobrecarregar igualdades de operador em ValueType.Equals substituídos](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)