---
title: "Guia Arquivo de Pagina&#231;&#227;o, Caixa de di&#225;logo Propriedades do Processo | Microsoft Docs"
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
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Arquivo de Pagina&#231;&#227;o, Caixa de di&#225;logo Propriedades do Processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o  **O arquivo de página** guia para examinar o arquivo de paginação de um processo.  Para exibir o  [Caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mover o foco para um  [Processos de modo de exibição](../debugger/processes-view.md) janela.  Selecione qualquer nó do processo na árvore e escolha  **Propriedades** da  **Exibir** menu.  
  
 As configurações a seguir estão disponíveis na  **Arquivo de página** guia:  
  
|Entrada|Descrição|  
|-------------|---------------|  
|**Bytes do arquivo de paginação**|O número atual de páginas que esse processo está usando no arquivo de paginação.  O arquivo de paginação armazena páginas de dados usada pelo processo, mas não contidas em outros arquivos.  O arquivo de paginação é usado por todos os processos e falta de espaço no arquivo de paginação pode causar erros durante a execução de outros processos.|  
|**Máximo de Bytes de arquivo de paginação**|O número máximo de páginas que este processo usou no arquivo de paginação.|  
|**Falhas de página**|O número de falhas de página por segmentos em execução neste processo.  Uma falha de página ocorre quando um thread refere\-se a uma página de memória virtual que não esteja no conjunto de trabalho na memória principal.  Assim, a página não será recuperada do disco se ele estiver na lista de espera e, portanto, já na memória principal, ou se ele está sendo usado por outro processo com a página for compartilhada.|