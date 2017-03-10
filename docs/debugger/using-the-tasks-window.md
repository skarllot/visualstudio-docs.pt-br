---
title: "Usando a janela Tarefas | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.paralleltasks"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, janela de tarefas paralelas"
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usando a janela Tarefas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O **tarefas** janela é semelhante a **Threads** janela, exceto que mostra informações sobre <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task\_handle](../Topic/task_group%20Class.md), ou [WinJS. Promise](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) objetos em vez de cada thread.  Como threads, as tarefas representam as operações assíncronas que podem ser executadas simultaneamente; no entanto, várias tarefas podem ser executadas no mesmo thread.  Consulte [programação assíncrona em JavaScript \(aplicativos da Windows Store\)](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) para obter mais informações.  
  
 No código gerenciado, você pode usar a janela **Tarefas** quando trabalha com objetos <xref:System.Threading.Tasks.Task?displayProperty=fullName> ou com as palavras\-chave **await** e **async** \(**Await** e **Async** no Visual Basic\).  Para obter mais informações sobre as tarefas no código gerenciado, consulte  [Programação paralela](../Topic/Parallel%20Programming%20in%20the%20.NET%20Framework.md).  
  
 No código nativo, você pode usar a janela **Tarefas** quando trabalha com [grupos de tarefas](/visual-cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algoritmos paralelos](/visual-cpp/parallel/concrt/parallel-algorithms), [agentes assíncronas](/visual-cpp/parallel/concrt/asynchronous-agents), e [tarefas leves](/visual-cpp/parallel/concrt/task-scheduler-concurrency-runtime).  Para obter mais informações sobre as tarefas no código nativo, consulte [Tempo de Execução de Simultaneidade](/visual-cpp/parallel/concrt/concurrency-runtime).  
  
 No JavaScript, você pode usar a janela tarefas quando você estiver trabalhando com código de .then promessa.  
  
 Você pode usar a janela **Tarefas** sempre que quebrar no depurador.  Você poderá acessá\-la clicando no menu **Depurar**, **Janelas** e **Tarefas**.  A ilustração a seguir mostra a janela **Tarefas** no modo padrão.  
  
 ![Janela tarefas paralelas](../debugger/media/parallel_tasks_window.png "Parallel\_Tasks\_Window")  
  
> [!NOTE]
>  No código gerenciado, um <xref:System.Threading.Tasks.Task> que tem um status de <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus> ou <xref:System.Threading.Tasks.TaskStatus> podem não ser exibidos na janela das tarefas quando os threads gerenciados estão em um estado de suspensão ou junção.  
  
## Informações da coluna de tarefas  
 As colunas na janela **Tarefas** mostram as informações a seguir.  
  
|Nome da Coluna|Descrição|  
|--------------------|---------------|  
|**Sinalizadores**|Mostra quais tarefas estão sinalizadas e permite sinalizar ou remover a sinalização de uma tarefa.|  
|**Ícones**|Uma seta amarela indica a tarefa atual.  A tarefa atual é a tarefa mais alta no thread atual.<br /><br /> Uma seta branca indica a tarefa de quebra, isto é, a que era atual quando o depurador foi chamado.<br /><br /> O ícone de pausa indica uma tarefa que foi congelada pelo usuário.  Você pode congelar e descongelar uma tarefa clicando com o botão direito na lista.|  
|**ID**|Um número fornecido pelo sistema para a tarefa.  No código nativo, esse é o endereço da tarefa.|  
|**Status**|O estado atual \(agendado, ativo, com deadlock, aguardando ou concluído\) da tarefa.  Uma tarefa agendada é aquela que ainda não foi executada e, portanto, ainda não tem uma pilha de chamadas, um thread alocado ou as informações relacionadas.<br /><br /> Uma tarefa ativa é aquela que estava executando código antes de quebrar no depurador.<br /><br /> Uma tarefa de espera é aquele que está bloqueado porque está aguardando um evento deve ser sinalizado, um bloqueio ser liberado ou outra tarefa ser concluída.<br /><br /> Uma tarefa com deadlock é uma tarefa de espera cujo thread está bloqueado com outro thread.<br /><br /> Passe o mouse sobre a célula **Status** para uma tarefa com deadlock ou em espera para ver mais informações sobre o bloqueio. **Warning:**  Os relatórios da janela **Tarefas** reporta deadlock apenas uma tarefa bloqueada que usa um primitivo de sincronização com suporte do WCT \(Passagem de Cadeia de Espera\).  Por exemplo, para um objeto <xref:System.Threading.Tasks.Task> com deadlock, que usa WCT, o depurador informa **Aguardando\-com deadlock**.  Para uma tarefa com deadlock que é gerenciada pelo Tempo de Execução de Simultaneidade, que não usa WCT, o depurador informa **Aguardando**.  Para obter mais informações sobre o WCT, consulte [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Hora de Início**|A hora em que a tarefa se tornou ativa.|  
|**Duração**|O número de segundos que a tarefa esteve ativa.|  
|**Hora de conclusão**|A hora em que a tarefa foi concluída.|  
|**Local**|O local atual da pilha de chamadas da tarefa.  Passe o mouse sobre esta célula para ver a pilha de chamada inteira para a tarefa.  As tarefas agendadas não têm um valor nessa coluna.|  
|**Tarefa**|O método inicial e quaisquer argumentos que são passados para a tarefa quando ela foi criada.|  
|**Pai**|A ID da tarefa que criou essa tarefa.  Se estiver em branco, a tarefa não terá pai.  Isso é aplicável somente para programas gerenciados.|  
|**Atribuição de Thread**|O nome e a ID do thread no qual a tarefa está em execução.|  
|**Retornar Status**|O status da tarefa quando foi concluída.  Os valores de retorno de status são **Êxito**, **Cancelado**, e **Erro**.|  
|**AppDomain**|Para código gerenciado, o domínio de aplicativo no qual a tarefa está em execução.|  
|**task\_group**|Para o código nativo, o endereço do objeto [task\_group](../Topic/task_group%20Class.md) que agendou a tarefa.  Para agentes assíncronos e tarefas leves, essa coluna é definida como 0.|  
|Processo|A ID do processo no qual a tarefa está em execução.|  
|Estado assíncrono|Para código gerenciado, o status da tarefa.  Por padrão, essa coluna está ocultada.  Para exibir esta coluna, abra o menu de contexto para um dos cabeçalhos de coluna.  Escolha **Colunas**, **AsyncState**.|  
  
 Você pode adicionar colunas à exibição clicando com o botão direito em um cabeçalho de coluna e selecionando as colunas desejadas.  \(Remover colunas desmarcando as seleções.\) Você também pode reordenar colunas arrastando\-os esquerda ou direita.  O menu de atalho da coluna é mostrado na ilustração a seguir.  
  
 ![Menu de contexto tarefas paralelas](../debugger/media/parallel_tasks_contextmenu.png "Parallel\_Tasks\_ContextMenu")  
  
## Tarefas de classificação  
 Para classificar as tarefas por critérios da coluna, clique no cabeçalho da coluna.  Por exemplo, clicando no cabeçalho de coluna **ID**, você poderá classificar as tarefas pela ID de tarefa: 1, 2, 3, 4, 5 e assim por diante.  Para inverter a ordem de classificação, clique no cabeçalho da coluna novamente.  A coluna e a ordem de classificação atuais estão indicadas por uma seta na coluna.  
  
## Agrupando tarefas  
 Você pode agrupar tarefas com base em qualquer coluna na exibição de lista.  Por exemplo, ao clicar com o botão direito no cabeçalho da coluna **Status** e clicar em **Agrupar por Status**, você pode agrupar todas as tarefas que têm o mesmo status.  Por exemplo, você pode visualizar rapidamente as tarefas em espera para que poder se concentrar em por que estão bloqueadas.  Você também pode recolher um grupo que não é de interesse durante a sessão de depuração.  Da mesma forma, você pode agrupar por outras colunas.  Um grupo pode ser sinalizado ou ter a sinalização removida apenas clicando no botão ao lado do cabeçalho do grupo.  A ilustração a seguir mostra a janela **Tarefas** no modo agrupado.  
  
 ![Modo agrupado de tarefas paralelas](../debugger/media/parallel_tasks_groupedmode.png "Parallel\_Tasks\_GroupedMode")  
  
## Modo de Exibição Pai\-Filho  
 \(Essa exibição está disponível apenas para código gerenciado.\) Um título de coluna e, em seguida, clicando em **exibição pai\-filho**, você pode alterar a lista de tarefas para uma exibição hierárquica, na qual cada filho tarefa é um subnó que pode ser exibido ou ocultado em seu pai.  A ilustração a seguir mostra as tarefas na exibição de pai\-filho.  
  
 ![Modo de exibição de pai&#45;filho de tarefas paralelas](../debugger/media/parallel_tasks_parentchildview.png "Parallel\_Tasks\_ParentChildView")  
  
## Tarefas de sinalização  
 Você pode sinalizar o thread no qual uma tarefa está sendo executada selecionando o item da lista de tarefas e escolhendo **Sinalizar** no menu de contexto, ou clicando no ícone de sinalizador na primeira coluna.  Se você sinalizar várias tarefas, poderá classificar na coluna do sinalizador para levar todas as tarefas sinalizadas para o alto para que você possa se concentrar apenas nelas.  Você também pode usar a janela **Pilhas Paralelas** para exibir apenas tarefas sinalizadas.  Isso permite filtrar tarefas nas quais você não está interessado para depuração.  Os sinalizadores não são mantidos entre sessões de depuração.  
  
## Congelando e descongelando tarefas  
 Você pode congelar o thread no qual uma tarefa está sendo executada clicando com botão direito no item da lista de tarefas e clicando em **Congelar Thread Atribuído**.  \(Se uma tarefa já está congelada, o comando é **Descongelar Thread atribuído**.\) Quando você congela um thread, esse thread não será executado quando você percorre o código após o ponto de interrupção atual.  O comando **Congelar Todos os Threads Exceto Esse** congelará todos os threads com exceção do que está executando o item da lista de tarefas.  
  
 A ilustração a seguir mostra os outros itens de menu para cada tarefa.  
  
 ![Menu de contexto tarefas paralelas](../debugger/media/parallel_tasks_contextmenu2.png "Parallel\_Tasks\_ContextMenu2")  
  
## Consulte também  
 [Noções básicas do depurador](../debugger/debugger-basics.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)   
 [Programação paralela](../Topic/Parallel%20Programming%20in%20the%20.NET%20Framework.md)   
 [Tempo de Execução de Simultaneidade](/visual-cpp/parallel/concrt/concurrency-runtime)   
 [Usando a janela Pilhas Paralelas](../debugger/using-the-parallel-stacks-window.md)   
 [Instruções passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)