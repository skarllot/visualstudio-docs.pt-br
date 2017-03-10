---
title: "Como criar um relat&#243;rio de rastreamento de chamada das ferramentas de cria&#231;&#227;o de perfil | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ETW [Visual Studio ALM], exibindo dados"
  - "ferramentas de desempenho, exibindo dados de ETW"
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como criar um relat&#243;rio de rastreamento de chamada das ferramentas de cria&#231;&#227;o de perfil
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O  *relatório de rastreamento de chamada* para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Ferramentas de Criação de Perfil lista informações de tempo para cada ponto de entrada e saída nas funções do seu aplicativo e cada chamada a outras funções por sua função.  Os relatórios de rastreamento de chamada estão disponíveis para analisar dados somente se foi coletado com o método de instrumentação.  
  
> [!NOTE]
>  Você não pode exibir relatórios de rastreamento de chamada no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Você deve usar a ferramenta de linha de comando **VSPerfReport** para gerar um arquivo de valores separados por vírgula \(.csv\) ou o arquivo XML.  Para obter mais informações sobre essa ferramenta, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
### Para criar um relatório de rastreamento de chamada  
  
1.  Abra uma janela de **Prompt de Comando**.  
  
2.  No prompt de comando, digite o seguinte comando:  
  
     *ToolsPath* **VSPerfReport** *VSPFile* **\/CallTrace \[\/Xml\]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|O caminho das ferramentas de linha de comando das Ferramentas de Criação de Perfil.  Para obter mais informações, consulte [Especificando o caminho para ferramentas de linha de comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Para analisar o arquivo de dados \(.vsp ou .vsps\).  Caminhos completos e parciais são aceitos.|  
    |Xml|Gera um relatório em formato XML.|  
  
## Consulte também  
 [Como coletar dados de Rastreamento de Eventos para Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)   
 [APIs de ferramentas de criação de perfil](../profiling/profiling-tools-apis.md)