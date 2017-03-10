---
title: "Grava&#231;&#227;o da fun&#231;&#227;o de gancho de depura&#231;&#227;o | Microsoft Docs"
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
  - "vc.hooks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "funções de gancho de depuração"
  - "depurando [C++], Suporte à depuração CRT"
  - "depuração [CRT], funções de gancho de depuração"
  - "ganchos"
  - "ganchos, depurar"
ms.assetid: 5510635f-cf69-4907-b72d-ae27af1f19af
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Grava&#231;&#227;o da fun&#231;&#227;o de gancho de depura&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta seção descreve várias funções de gancho de depuração personalizadas que você pode escrever que permitem inserir seu código em alguns pontos predefinidos no processamento normal do depurador.  
  
## Nesta seção  
 [Funções de gancho do bloco de cliente](../debugger/client-block-hook-functions.md)  
 Fornece orientação e um protótipo para escrever funções que validam ou reportam o conteúdo dos dados armazenados nos blocos \_CLIENT\_BLOCK.  
  
 [Funções de gancho de alocação](../debugger/allocation-hook-functions.md)  
 Define uma função de gancho de alocação, explora seus usos diferentes, indica limitações e fornece um protótipo.  
  
 [Ganchos de alocação e alocações de memória de CRT](../debugger/allocation-hooks-and-c-run-time-memory-allocations.md)  
 Descreve a limitação de funções de gancho de alocação de ignorar explicitamente blocos de `_CRT_BLOCK` se eles fizerem chamadas para as funções da biblioteca em tempo de execução C que alocam a memória interna.  Este tópico também listará as consequências se seu gancho de alocação não ignorar os blocos de `_CRT_BLOCK` \(com exemplos\) e como alterar a função padrão de gancho de alocação, **CrtDefaultAllocHook**.  
  
 [Funções de gancho de relatório](../debugger/report-hook-functions.md)  
 Discute `_CrtSetReportHook`, que você pode usar para filtrar relatórios para enfatizar tipos específicos de alocações.  Este tópico também fornece um protótipo.  
  
## Seções relacionadas  
 [Técnicas de depuração do CRT](../debugger/crt-debugging-techniques.md)  
 Links para técnicas de depuração para a biblioteca em tempo de execução C, incluindo o uso da biblioteca de depuração do CRT, macros para relatório, diferenças entre `malloc` e `_malloc_dbg`, escrevendo funções de gancho de depuração, e o heap de depuração do CRT.