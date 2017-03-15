---
title: "Guia Geral, Caixa de di&#225;logo Propriedades do Thread | Microsoft Docs"
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
  - "propriedades de thread"
  - "threading [Visual Studio], propriedades de thread"
ms.assetid: 46b6c668-6786-456e-97dc-337bcac0d812
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia Geral, Caixa de di&#225;logo Propriedades do Thread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Use essa caixa de diálogo para obter mais informações sobre um segmento específico.  Para exibir esta caixa de diálogo, mova o foco para um  [Visualização de Threads](../debugger/threads-view.md) janela ou abrir  [o modo de exibição de mensagens](../debugger/messages-view.md) e expandir uma mensagem.  Selecione qualquer nó do thread na árvore e escolha  **Propriedades** da  **Exibir** menu.  
  
 O  **Propriedades de segmento** caixa de diálogo contém um painel, o  **Geral** guia.  As configurações a seguir estão disponíveis:  
  
|Entrada|Descrição|  
|-------------|---------------|  
|**Module Name**|O nome do módulo.|  
|**Identificação do Segmento**|A identificação exclusiva deste segmento.  Observe que os números de identificação de segmento são reutilizados; Elas identificam um segmento somente para a vida útil do thread.|  
|**Process ID**|A identificação exclusiva desse processo.  Os números de identificação de processo são reutilizados identificam um processo somente para o tempo de vida do processo.  O tipo de objeto do processo é criado quando um programa é executado.  Todos os threads em um processo compartilham o mesmo espaço de endereço e têm acesso aos mesmos dados.  Escolha esse valor para exibir as propriedades do ID do processo.|  
|**Estado do segmento**|O estado atual do segmento.  Um thread de execução é utilizar um processador. um segmento em espera está prestes a usar um.  Um Thread pronto está esperando para usar um processador como um não é gratuito.  Um segmento em transição está aguardando um recurso executar, como, por exemplo, aguardando sua pilha de execução ser paginada a partir do disco.  Um segmento em espera não é necessário o processador porque está aguardando a conclusão de uma operação de periférica ou um recurso fique livre.|  
|**Razão de espera.**|Isso é aplicável somente quando o thread está em estado de espera.  Pares de evento são usados para comunicação com subsistemas protegidos.|  
|**Tempo de CPU**|Tempo de CPU total gasto com esse processo e seus segmentos.  Igual ao tempo de usuário \+ tempo privilegiado.|  
|**Tempo de usuário**|O tempo total decorrido que este segmento gastou executando código em modo de usuário.  Aplicativos são executados no modo de usuário, como fazem os subsistemas, como o Gerenciador de janelas e o mecanismo de gráficos.|  
|**Tempo privilegiado**|O tempo total decorrido que este segmento gastou executando código em modo privilegiado.  Quando um serviço de sistema do Windows é chamado, o serviço geralmente será executado no modo privilegiado para obter acesso a dados privados do sistema.  Esses dados são protegidos contra o acesso por threads em execução no modo de usuário.  Chamadas ao sistema podem ser explícitas ou eles podem ser implícitos, como, por exemplo, quando ocorre uma falha de página ou uma interrupção.|  
|**Elapsed Time**|O tempo total decorrido \(em segundos\) este thread está sendo executado.|  
|**Prioridade atual**|A prioridade dinâmica atual deste segmento.  Segmentos dentro de um processo podem aumentar e diminuir a sua própria prioridade básica em relação à prioridade básica do processo.|  
|**Prioridade básica**|A prioridade básica atual deste segmento.|  
|**Endereço inicial**|Iniciando endereço virtual para este segmento.|  
|**PC do usuário**|O contador do programa de usuário para o segmento.|  
|**Alternâncias de contexto**|O número de alternâncias de um thread para outro.  As alternâncias de thread podem ocorrer dentro de um único processo ou através dos processos.  Uma alternância de thread pode ser causada por um thread solicitando informações a outro ou por um thread sendo apropriado quando um segmento de maior prioridade torna\-se pronto para ser executado.|