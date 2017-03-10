---
title: "Criando relat&#243;rios do criador de perfil a partir da linha de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Criando relat&#243;rios do criador de perfil a partir da linha de comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A ferramenta de linha de comando **VSPerfReport** permite criar ou .xml o arquivo CSV \(.csv\) informa de arquivos de dados de perfil .vsp \(\).  Os tipos de relatórios de VSPerfReport correspondem a exatidão com a qual as exibições com base em interface para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Você pode filtrar o relatório para mostrar somente seu código e para mostrar apenas um segmento de arquivo de dados de perfil.  Para obter mais informações, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
 Você também pode tornar seus arquivos de dados de perfil compartilhar inserindo símbolos nos arquivos de .vsp e criando os arquivos previamente analisados de relatório \(.vsps\) que são menores e mais rápidos abrir.  
  
## Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|------------|--------------------------|  
|**Criar um relatório básico.** Criar todos ou um subconjunto dos tipos de relatórios de VSPerfReport.|-   [Criando relatórios básicos](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Compara dois arquivos de dados de perfil.** Crie um relatório de “diff” que compara dados de desempenho em dois arquivos de dados de perfil.|-   [Como criar um relatório de comparação de criador de perfil a partir de um prompt de comando](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Exibir o rastreamento de chamadas e o rastreamento de eventos de dados do windows \(ETW\).** Crie um relatório de rastreamento de chamada que lista as informações de controle de tempo para cada ponto de entrada e saída às funções do aplicativo e o cada chamada para outras funções pela função.  Ou crie uma lista detalhada de todos os eventos de ETW que foram coletados em analisar executado.|-   [Como criar um relatório de rastreamento de chamada](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrar um relatório.** Limite um relatório somente a funções em seu código ou a um momento específico nos dados de perfil arquivo.|-   [Como filtrar relatórios a partir da linha de comando](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Crie arquivos de dados portáteis de perfil.** Para facilitar o compartilhamento de dados do perfil, você pode inserir os símbolos para analisar executado no arquivo de .vsp.  Você também pode criar um arquivo de analisar os dados de criação de perfil .vsps \(\) que é menor e mais rápido abrir.|-   [Criando arquivos de dados de criação de perfil móveis](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|