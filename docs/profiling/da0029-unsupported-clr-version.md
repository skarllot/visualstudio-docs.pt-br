---
title: "DA0029: vers&#227;o do CLR sem suporte | Microsoft Docs"
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
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0029: vers&#227;o do CLR sem suporte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificação da Regra|DA0029|  
|Categoria|Uso de Ferramentas de Criação de Perfil|  
|Método de criação de perfil|Analisar de linha de comando|  
|Message \(Mensagem\)|Uma versão sem suporte do CLR foi detectada durante a coleção.  Os símbolos gerenciadas não pode resolver corretamente.|  
|Tipo de regra|Informações.|  
  
## Causa  
 Você está tentando analisar um aplicativo que usa [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] que não tem suporte pelas Ferramentas de Criação de Perfil.  
  
## Descrição da Regra  
 Esse aviso ocorre porque as ferramentas de criação de perfil não poderão de resolver símbolos para o código gerenciado no aplicativo.  As ferramentas de criação de perfil não pode resolver símbolos de código gerenciado para os aplicativos que estão em execução [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  
  
## Como Corrigir Violações  
 Nenhum.