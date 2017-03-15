---
title: "CA2103: revisar seguran&#231;a obrigat&#243;ria | Microsoft Docs"
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
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103: revisar seguran&#231;a obrigat&#243;ria
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Categoria|Microsoft.Security|  
|Alteração Significativa|Quebra|  
  
## Causa  
 Um método usa a segurança obrigatória e pode construir a permissão usando as informações do estado ou os valores de retorno que podem ser alteradas desde que a demanda está ativa.  
  
## Descrição da Regra  
 O usa obrigatórios de segurança objetos gerenciados para especificar permissões e ações de segurança durante a execução do código, comparada à segurança declarativa, que usa atributos para armazenar permissões e ações nos metadados.  A segurança obrigatória é bem flexível como você pode definir o estado de um objeto de permissão e selecione ações de segurança usando informações não disponíveis até o tempo de execução.  Junto com essa flexibilidade o risco de informações de tempo de execução que você usa para determinar o estado de uma permissão não permanece inalterado à medida que a ação é aplicado.  
  
 Use a segurança declarativa sempre que possível.  As demandas declarativa são mais fáceis de entender.  
  
## Como Corrigir Violações  
 Revise as demandas obrigatórias de segurança para garantir que o estado de permissão não confie nas informações que pode ser modificado desde a permissão está sendo usada.  
  
## Quando Suprimir Alertas  
 É seguro suprimir um aviso dessa regra se a permissão não confie em alterar dados.  Porém, é melhor alterar a demanda obrigatória para seu equivalente declarativo.  
  
## Consulte também  
 [Diretrizes de codificação segura](../Topic/Secure%20Coding%20Guidelines.md)   
 [Dados e modelagem](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)