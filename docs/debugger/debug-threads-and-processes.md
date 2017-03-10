---
title: "Depurar threads e processos no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurando [Visual Studio], threads"
  - "depurando threads"
  - "depuração multiprocesso"
  - "processos, depuração"
  - "threading [Visual Studio], depuração"
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 15
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurar threads e processos no Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Threads* e *processos* são conceitos relacionados à ciência da computação.  Ambos representam sequências de instruções que devem executar em uma ordem específica.  Instruções em threads ou processos separados, entretanto, podem ser executados em paralelo.  
  
 Os processos existem no sistema operacional e correspondem ao que os usuários veem como programas ou aplicativos.  Um thread, por outro lado, existe dentro de um processo.  Por esse motivo, os threads são às vezes chamados de *processos leves*.  Cada processo consiste em um ou mais threads.  
  
 A existência de vários processos permite que um computador execute mais de uma tarefa de cada vez.  A existência de vários threads permite que um processo separe o trabalho a ser executado paralelamente.  Em um computador com multiprocessadores, os processos ou threads podem ser executados em processadores diferentes.  Isso permite o verdadeiro processamento paralelo.  
  
 O processamento paralelo perfeito não é sempre possível.  Às vezes os threads devem ser sincronizados.  Um thread pode ter que aguardar um resultado de outro thread, ou um thread pode precisar de acesso exclusivo a um recurso que outro thread está usando.  Problemas de sincronização são uma causa comum de erro em aplicativos com multithreads.  Em alguns casos, os threads podem interromper espera de um recurso que nunca fica disponível.  Isso resulta em uma condição chamada *deadlock*.  
  
 O depurador do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] fornece ferramentas avançadas e mas fáceis de usar para depurar threads e processos.  
  
## Ferramentas para depurar threads e processos no Visual Studio  
 As principais ferramentas para trabalhar com processos no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] são a caixa de diálogo **Anexar ao Processo**, a janela de **Processos**, e a barra de ferramentas **Local de Depuração**.  As ferramentas principais para depurar threads são a janela de **Threads**, marcadores de thread em janelas de origem, e a barra de ferramentas de **Local de Depuração**.  
  
 As ferramentas principais para depurar aplicativos multissegmentados são **Pilhas Paralelas** e **Tarefas Paralelas**, **Inspeção Paralela**, e as janelas de **Threads da GPU**.  
  
 A tabela a seguir mostra as informações disponíveis e as ações que você pode executar em cada um desses locais:  
  
|Interface do Usuário|Informação disponível|Ações que você pode executar|  
|--------------------------|---------------------------|----------------------------------|  
|Caixa de diálogo **Anexar ao Processo**|Processos disponíveis você pode anexar:<br /><br /> -   Nome do Processo \(exe\)<br />-   Número de identificação de processo<br />-   Título da barra de menus<br />-   Tipo \(v4.0 gerenciado; V2.0 gerenciado, v1.1, v1.0; x86; x64; IA64\)<br />-   Nome de usuário \(nome de conta\)<br />-   Número da sessão|Selecione um processo anexar.<br /><br /> Selecione um computador remoto<br /><br /> Altere o tipo de transporte para se conectar a computadores remotos|  
|Janela **Processos**|Processos anexados:<br /><br /> -   Nome do Processo<br />-   Número de identificação de processo<br />-   Caminho para processar .exe<br />-   Título da barra de menus<br />-   Estado \(interrupção.  em execução\)<br />-   Depurando \(nativo, gerenciado etc.\)<br />-   Tipo de transporte \(padrão, nativo sem autenticação\)<br />-   Qualificador de transporte \(computador remoto\)|Ferramentas:<br /><br /> -   Attach<br />-   Detach<br />-   Terminate<br /><br /> O menu de atalho:<br /><br /> -   Attach<br />-   Detach<br />-   Desanexe quando a depuração for interrompida<br />-   Terminate|  
|**Janela** de Threads|Threads durante o processo atual:<br /><br /> -   Identificação do Thread<br />-   ID gerenciada<br />-   Categoria \(thread principal, thread de interface, manipulador de chamada de procedimento remoto ou thread de trabalho\)<br />-   Nome do Thread<br />-   Local onde o thread é criado<br />-   Prioridade<br />-   Máscara de Afinidade<br />-   Contagem suspensa<br />-   Nome do Processo<br />-   Indicador de Sinalização<br />-   Indexador suspenso|Ferramentas:<br /><br /> -   Pesquisar<br />-   Pesquisar pilha de chamadas<br />-   Sinalizar Apenas Meu Código<br />-   Sinalizar Seleção de Módulo Personalizada<br />-   Group by<br />-   Colunas<br />-   Expandir\/Recolher pilhas de chamadas<br />-   Expandir\/Recolher grupos<br />-   Congelar\/descongelar threads<br /><br /> O menu de atalho:<br /><br /> -   Mostrar threads na origem<br />-   Alternar para um segmento<br />-   Congelar um thread em execução<br />-   Descongelar um thread congelado<br />-   Sinaliza um thread para estudos adicionais<br />-   Remover a sinalização de um segmento<br />-   Renomear um thread<br />-   Exibir e ocultar threads<br /><br /> Outras ações:<br /><br /> -   Exibir a pilha de chamadas para um segmento em um DataTip|  
|Janela de origem|Indexadores de threads na medianiz esquerda indicam um ou vários segmentos \(desativado por padrão, ativado usando o menu de atalho na janela **Threads**\)|O menu de atalho:<br /><br /> -   Alternar para um segmento<br />-   Sinaliza um thread para estudos adicionais<br />-   Remover a sinalização de um segmento|  
|Barra de ferramentas **Local de Depuração**|-   Processo atual<br />-   Mostrar a miniatura do aplicativo<br />-   Suspenda o aplicativo<br />-   Retomar o aplicativo<br />-   Suspenda e feche o aplicativo<br />-   Thread atual<br />-   Alterne o estado atual do sinalizador do segmento<br />-   Mostrar somente threads sinalizados<br />-   Mostrar o só o processo atual<br />-   Quadro de pilha atual|-   Alternar para outro processo<br />-   Suspenda, retome ou feche o aplicativo<br />-   Alterne para outro thread no processo atual<br />-   Alterne para outro quadro de pilha no thread atual<br />-   Sinalizar ou remover sinalização de threads atuais<br />-   Mostrar somente threads sinalizados<br />-   Mostrar somente o processo atual|  
|Janela de **Pilhas Paralelas**|-   Pilhas de chamadas para vários threads em uma janela.<br />-   Quadro de pilha ativo para cada segmento.<br />-   Chamadores e receptores de qualquer método.|-   Remover threads especificados<br />-   Alterne para modo de exibição de Tarefas paralelas<br />-   Sinalizar ou remover sinalização de um thread<br />-   Aplicar zoom|  
|Janela **Tarefas Paralelas**|-   Exibir informações sobre os objetos de <xref:System.Threading.Tasks.Task>, incluindo ID de tarefa, status de tarefa \(agendada, executando, em espera, em deadlock\), e qual segmento está atribuído à tarefa.<br />-   Local atual na pilha de chamadas.<br />-   O delegado passado para a tarefa no horário de criação|-   Alterne para a tarefa atual<br />-   Sinalizar ou remover sinalização de uma tarefa<br />-   Congelar ou descongelar uma tarefa|  
|Janela **Inspeção Paralela** window|-   A coluna do sinalizador, na qual você pode marcar um thread ao qual deseja prestar atenção especial.<br />-   A coluna do quadro, na qual uma seta indica o quadro selecionado.<br />-   Uma coluna configurável que pode exibir o computador, o processo, o bloco, a tarefa e o thread.|-   Sinalizar ou remover sinalização de um thread<br />-   Exibir somente threads sinalizados<br />-   Quadros de opção<br />-   Classificar uma coluna<br />-   Agrupar threads<br />-   Congelar ou descongelar threads<br />-   exporte os dados na janela de Inspeção Paralela|  
|Janela **Threads da GPU**|-   A coluna do sinalizador, na qual você pode marcar um thread ao qual deseja prestar atenção especial.<br />-   A coluna thread ativo, em que uma seta amarela indica um thread ativo.  Uma seta indica um thread onde a execução interrompe no depurador.<br />-   A coluna **Contagem de Threads**, que exibe o número de segmentos no mesmo local.<br />-   A coluna de **Linha**, que exibe a linha de código onde cada grupo de segmentos está localizado.<br />-   A coluna de **Endereço**, que exibe o endereço da instrução onde cada grupo de threads está localizado.<br />-   A coluna **Local**, que é o local no código do endereço.<br />-   A coluna **Status**, que mostra se o segmento está ativo ou bloqueado.<br />-   A coluna **Lado a lado**, que mostra o índice lado a lado para os segmentos na linha.|-   Altere para um thread ativo diferente<br />-   Exibir um determinado ladrilho e o thread<br />-   Exibir ou ocultar uma coluna<br />-   Classificar por coluna<br />-   Agrupar threads<br />-   Congelar ou descongelar threads<br />-   Sinalizar ou remover sinalização de um thread<br />-   Exibir somente threads sinalizados|  
  
## Consulte também  
 [Anexar a processos em execução](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Depurar aplicativos multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Depurando código de GPU](../debugger/debugging-gpu-code.md)