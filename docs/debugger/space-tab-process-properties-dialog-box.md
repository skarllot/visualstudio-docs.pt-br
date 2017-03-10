---
title: "Guia Espa&#231;o, Caixa de di&#225;logo Propriedades do Processo | Microsoft Docs"
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
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Espa&#231;o, Caixa de di&#225;logo Propriedades do Processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o  **espaço** guia para examinar o espaço de endereço de um processo.  Para exibir o  [Caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mover o foco para um  [Processos de modo de exibição](../debugger/processes-view.md) janela.  Selecione qualquer nó do processo na árvore e escolha  **Propriedades** da  **Exibir** menu.  
  
 As configurações a seguir estão disponíveis na  **espaço** guia:  
  
|Entrada|Descrição|  
|-------------|---------------|  
|**Apresentação para os espaços marcados como**|Use esta caixa de listagem para selecionar a categoria de espaço \(imagem mapeada, reservados ou não atribuído\).|  
|**Bytes executáveis**|Para a categoria selecionada, a soma de todo o espaço de endereço que esse processo está usando.  Memória executável é aquela que pode ser executada por programas, mas pode não ser lidos ou gravada.|  
|**Bytes de EXEC\-somente leitura**|Para a categoria selecionada, a soma de todo o espaço de endereço em uso com as propriedades somente leitura que esse processo está usando.  EXEC\-memória somente leitura é a memória que pode ser executada, bem como ler.|  
|**Bytes de EXEC e leitura \/ gravação.**|Para a categoria selecionada, a soma de todo o espaço de endereço em uso com propriedades de leitura e gravação que esse processo está usando.  Memória de EXEC e leitura \/ gravação é aquela que pode ser executada pelos programas, bem como lida e modificada.|  
|**Bytes de cópia de gravação de EXEC**|Para a categoria selecionada, a soma de todo o espaço de endereço que pode ser executada pelos programas, bem como lida e gravada.  Esse tipo de proteção é usado quando a memória precisa ser compartilhada entre processos.  Se os processos de compartilhamento apenas lerem a memória, todos eles usarão a mesma memória.  Se um processo de compartilhamento deseja acesso de gravação, será feita uma cópia da memória para o processo.|  
|**Bytes sem acesso**|Para a categoria selecionada, a soma de todo o espaço de endereço que impede que um processo de usá\-lo.  Uma violação de acesso é gerada se a gravação ou leitura é tentada.|  
|**Bytes de somente leitura**|Para a categoria selecionada, a soma de todo o espaço de endereço que pode ser executado, bem como ler.|  
|**Bytes de leitura\-gravação.**|Para a categoria selecionada, a soma de todo o espaço de endereço que permite a leitura e gravação.|  
|**Cópia de gravação Bytes**|Para a categoria selecionada, a soma de todo o espaço de endereço que permite compartilhamento de memória para leitura, mas não para gravação.  Quando processos estão lendo essa memória, eles podem compartilhar a mesma memória.  No entanto, quando um processo de compartilhamento deseja ter acesso de leitura\/gravação para essa memória compartilhada, é feita uma cópia do que a memória para gravação.|