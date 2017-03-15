---
title: "Guia Geral, Caixa de di&#225;logo Propriedades do Processo | Microsoft Docs"
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
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Geral, Caixa de di&#225;logo Propriedades do Processo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use o  **Geral** guia para obter mais informações sobre um processo específico.  Para exibir o  [Caixa de diálogo de propriedades do processo](../debugger/process-properties-dialog-box.md), mover o foco para um  [Processos de modo de exibição](../debugger/processes-view.md) janela.  Selecione qualquer nó do processo na árvore e escolha  **Propriedades** da  **Exibir** menu.  
  
 As configurações a seguir estão disponíveis na  **Geral** guia:  
  
|Entrada|Descrição|  
|-------------|---------------|  
|**Module Name**|O nome do módulo.|  
|**Process ID**|A identificação exclusiva desse processo.  Os números de identificação de processo são reutilizados identificam um processo somente para o tempo de vida do processo.  O tipo de objeto do processo é criado quando um programa é executado.  Todos os threads em um processo compartilham o mesmo espaço de endereço e têm acesso aos mesmos dados.|  
|**Base de prioridade**|A prioridade básica atual deste processo.  Segmentos dentro de um processo podem aumentar e diminuir a sua própria prioridade básica em relação à prioridade de base do processo.|  
|**Segmentos \(Threads\)**|O número de segmentos atualmente ativos neste processo.|  
|**Tempo de CPU**|Tempo de CPU total gasto com esse processo e seus segmentos.  Igual ao tempo de usuário mais tempo privilegiado.|  
|**Tempo de usuário**|O tempo decorrido cumulativo que segmentos do processo, este tem executaram código no modo de usuário em threads ocupados.  Aplicativos são executados no modo de usuário, como fazem os subsistemas como, por exemplo, o Gerenciador de janelas e o mecanismo de gráficos.|  
|**Tempo privilegiado**|O tempo total decorrido esse processo está sendo executado no modo privilegiado em threads ocupados.  A camada de serviço, as rotinas do executivo e Kernel executados no modo privilegiado.  Drivers de dispositivo para a maioria dos dispositivos diferentes de adaptadores gráficos e impressoras também executar no modo privilegiado.  Algum trabalho que o Windows para seu aplicativo pode aparecer em outros processos de subsistema além, ao tempo privilegiado.|  
|**Elapsed Time**|O tempo total decorrido que esse processo está em execução.|