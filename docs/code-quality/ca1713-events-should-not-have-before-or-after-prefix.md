---
title: "CA1713: os eventos n&#227;o devem ter um prefixo anterior ou posterior | Microsoft Docs"
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
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
  - "CA1713"
helpviewer_keywords: 
  - "CA1713"
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1713: os eventos n&#227;o devem ter um prefixo anterior ou posterior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Categoria|Microsoft.Naming|  
|Alteração Significativa|Quebra|  
  
## Causa  
 O nome de início de um evento com “antes de” ou “depois de”.  
  
## Descrição da Regra  
 Os nomes de evento devem descrever a ação que gerencie o evento.  Para nomear eventos relacionados que são gerados em uma sequência específica, use o tempo atual ou passado para indicar a posição relativa na sequência de ações.  Por exemplo, ao nomear um par de evento que é gerado ao fechar um recurso, você pode nomear o “que fecha” e “fechado”, em vez de “BeforeClose” e “AfterClose”.  
  
 Convenções de nomenclatura dão uma aparência comum para bibliotecas que tem como foco o common language runtime.  Isto reduz a curva de aprendizado que é necessária para novas bibliotecas de software, e aumenta confiança dos clientes de que a biblioteca foi desenvolvida por alguém que com experiência programar código gerenciado.  
  
## Como Corrigir Violações  
 Remova o prefixo do nome do evento, e considere\-a apenas alterar o nome para usar o tempo atual ou anterior de um verbo.  
  
## Quando Suprimir Alertas  
 Não elimine um alerta desta regra.