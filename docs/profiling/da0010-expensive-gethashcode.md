---
title: "DA0010: fun&#231;&#227;o GetHashCode dispendiosa | Microsoft Docs"
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
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0010: fun&#231;&#227;o GetHashCode dispendiosa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificação da Regra|DA0010|  
|Categoria|uso do .NET Framework|  
|Analisando métodos|Preparação de exemplos<br /><br /> Memória de .NET|  
|Message \(Mensagem\)|As funções de GetHashCode devem ser baixo e não atribuir nenhuma memória.  Reduzir a complexidade da função de código de hash se possível.|  
|Tipo de mensagem|Aviso|  
  
## Causa  
 Chamadas para o método de GetHashCode de classificação são uma proporção significativa de dados de perfil ou o método aloca memória.  
  
## Descrição da Regra  
 O hash é uma técnica para localizar rapidamente um item específico em uma grande coleção.  O como tabelas de hash pode ser muito grande e oferecem suporte a muito altas taxas de acesso, tabelas de hash deve ser muito eficiente.  Uma implicação deste requisito é que os métodos de GetHashCode no.NET Framework não precisam alocar memória.  Alocar memória aumenta a carga do coletor de lixo e expõe o método a atrasos em potencial se torna necessário executar a coleta de lixo no resultado da solicitação de alocação.  
  
## Como Corrigir Violações  
 Reduzir a complexidade do método.