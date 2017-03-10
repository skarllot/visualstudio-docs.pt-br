---
title: "DA0006: substituir Equals() para tipos de valor | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAOverrideEquals"
  - "vs.performance.6"
  - "vs.performance.DA0006"
  - "vs.performance.rules.DA0006"
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0006: substituir Equals() para tipos de valor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificação da Regra|DA0006|  
|Categoria|uso do .NET Framework|  
|Métodos de Profiiling|Preparação de exemplos|  
|Message \(Mensagem\)|Resultados de substituição e o operador de igualdade em tipos de valor.|  
|Tipo de Mensagem|Aviso|  
  
## Causa  
 Chamadas para o método de igual ou operadores de igualdade de um tipo de valor utilitário é uma proporção significativa de dados de perfil.  Considere implementar um método mais eficiente.  
  
## Descrição da Regra  
 Para tipos de valor, a implementação herdada de igual usa a biblioteca de <xref:System.Reflection> e compara o conteúdo de todos os campos no tipo.  Reflexão é computacionalmente cara, e comparar cada campo por igualdade pode ser desnecessário.  Se você espera que os usuários comparar ou classificar instâncias ou a usar como tabela de hash chaves, seu tipo de valor deve implementar iguais.  Se sua linguagem de programação oferece suporte à sobrecarga de operador, você também deve fornecer uma implementação dos operadores de igualdade e desigualdade.  
  
 Para obter mais informações sobre como substituir semelhantes e operadores de igualdade, consulte [Diretrizes para implementar semelhantes e o operador de igualdade \(\=\=\)](http://go.microsoft.com/fwlink/?LinkId=177818).  
  
## Como investigar um aviso  
 Para obter um exemplo da implementação dos resultados e operadores de igualdade, consulte a regra [CA1815: substituir igualdades e igualdades de operador em tipos de valor](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)de análise de código