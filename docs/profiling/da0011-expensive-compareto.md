---
title: "DA0011: fun&#231;&#227;o CompareTo dispendiosa | Microsoft Docs"
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
  - "vs.performance.DA0011"
  - "vs.performance.rules.DAExpensiveCompareTo"
  - "vs.performance.11"
  - "vs.performance.rules.DA0011"
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0011: fun&#231;&#227;o CompareTo dispendiosa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificação da Regra|DA0011|  
|Categoria|uso do .NET Framework|  
|Analisando métodos|Preparação de exemplos<br /><br /> Memória de .NET|  
|Message \(Mensagem\)|As funções CompareTo devem ser baixo e não atribuir nenhuma memória.  Reduzir a complexidade da função CompareTo se possível.|  
|Tipo de regra|Aviso|  
  
## Causa  
 O método CompareTo de tipo é caro ou aloca memória.  
  
## Descrição da Regra  
 Os métodos CompareTo devem ser eficientes e não precisam alocar memória.  
  
## Como Corrigir Violações  
 Reduzir a complexidade do método CompareTo.