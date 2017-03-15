---
title: "Guia Mem&#243;ria, Caixa de di&#225;logo Propriedades do Processo | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propriedades do processo para Windows NT"
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Mem&#243;ria, Caixa de di&#225;logo Propriedades do Processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o  **memória** guia para mostrar como um processo usa memória.  Para exibir o  [Caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mover o foco para um  [Processos de modo de exibição](../debugger/processes-view.md) janela.  Selecione qualquer nó do processo na árvore e escolha  **Propriedades** da  **Exibir** menu.  
  
 As configurações a seguir estão disponíveis na  **memória** guia:  
  
|Entrada|Descrição|  
|-------------|---------------|  
|**Bytes virtuais**|O tamanho atual \(em bytes\) do espaço de endereço virtual em que o processo está usando.  O uso do espaço de endereço virtual não implica necessariamente no uso correspondente de disco ou páginas de memória principal.  Entretanto, o espaço virtual é finito e muito uso pode limitar a capacidade do processo carregar bibliotecas.|  
|**Bytes de pico virtuais**|O número máximo de bytes de espaço de endereço virtual do processo usou a qualquer momento.|  
|**Conjunto de trabalho**|O conjunto de páginas de memória utilizadas recentemente pelos segmentos no processo.  Se a memória livre no computador estiver acima de um limite, páginas serão deixadas no conjunto de trabalho de um processo, mesmo que não estejam em uso.  Quando a memória livre cair abaixo de um limite, as páginas serão excluídas do conjunto de trabalho.  Se forem requisitadas, serão reinseridas no conjunto de trabalho\-falha de software antes de sair da memória principal.|  
|**Pico de conjunto de trabalho.**|O número máximo de páginas no conjunto de trabalho deste processo em qualquer ponto no tempo.|  
|**Bytes de Pool Paginado**|A quantidade atual de pool paginado o processo alocou.  Pool paginável é uma área de memória do sistema onde a componentes do sistema operacional adquirir espaço conforme eles realizar suas tarefas indicadas.  Páginas de memória paginável podem ser despaginadas para o arquivo de paginação quando não são acessados pelo sistema para períodos de tempo toleráveis.|  
|**Bytes de Pool não paginado**|O número atual de bytes do pool não\-paginável alocada pelo processo.  O pool não paginado é uma área de memória de sistema onde o espaço é adquirido pelos componentes do sistema operacional conforme eles realizar suas tarefas indicadas.  Páginas de pool não paginado não podem ser paginadas para o arquivo de paginação; eles permanecem na memória principal, enquanto estiverem alocados.|  
|**Bytes particulares**|O número atual de bytes que este processo alocou e que não pode ser compartilhado com outros processos.|  
|**Bytes livres**|O espaço total de endereço virtual não utilizados desse processo.|  
|**Bytes reservados**|A quantidade total de memória virtual, reservada para uso futuro por esse processo.|  
|**Bytes de imagem livres**|A quantidade de espaço de endereço virtual que não está em uso ou reservado por imagens no processo.|  
|**Bytes de imagem reservados**|A soma de toda a memória virtual reservado por imagens executadas dentro do processo.|