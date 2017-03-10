---
title: "Salvando e exportando o desempenho das ferramentas de dados | Microsoft Docs"
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
  - "ferramentas de desempenho, salvando e exportando relatórios"
ms.assetid: 2e9b28fe-3ed2-4e1d-b9cb-0a5e384380b0
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Salvando e exportando o desempenho das ferramentas de dados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Este tópico descreve como salvar e exportar arquivos de dados de desempenho.  
  
##  <a name="BKMK_Save_Profiler_Data_Files_As_Analyzed_Report_Files"></a> Como: salvar arquivos de dados de desempenho como arquivos de relatório analisados  
 Você pode salvar modos de exibição filtrados ou não filtrados de criação de perfil de arquivos de dados \(. vsp\) como arquivos de relatório analisado. \(VSPs\). Um arquivo de relatório analisado pode ser exibido na janela de exibição do relatório e é significativamente menor do que o arquivo. vsp original. No entanto, é possível aplicar um filtro aos dados de um arquivo. VSPs. Você pode criar um arquivo de relatório analisado do Performance Explorer sem abrir o arquivo no ambiente de desenvolvimento integrado \(IDE\), ou você pode abrir e filtrar o arquivo. vsp e, em seguida, salvar os resultados.  
  
#### Para salvar um relatório de desempenho analisados do Performance Explorer  
  
1.  Em **relatórios**, clique no arquivo de dados de criação de perfil que você deseja analisar e, em seguida, clique em **Salvar analisados**.  
  
2.  No **Salvar dados analisados** caixa de diálogo caixa, especifique o diretório e, em seguida, digite o nome do arquivo.  
  
3.  Clique em **Salvar.**  
  
#### Para salvar um relatório de desempenho analisados na janela de exibição de relatório  
  
1.  Abra o arquivo de dados \(. vsp\) a criação de perfil na janela de exibição do relatório.  
  
2.  \(Opcional\) Aplica um filtro aos dados. Para obter mais informações, consulte [Filtro de exibição do relatório de ferramentas de criação de perfil](../profiling/performance-report-view-filter.md).  
  
3.  Clique em **Salvar analisados** na barra de ferramentas de janela de exibição relatório.  
  
4.  No **Salvar dados analisados** caixa de diálogo caixa, especifique o diretório e, em seguida, digite o nome do arquivo.  
  
5.  Clique em **Salvar.**  
  
## Como: criação de perfil de exportação das ferramentas de relatórios para um. XML ou. Arquivo CSV  
 Você pode exportar uma ou mais exibições de relatório de um arquivo. vsp ou um arquivo de dados da criação de perfil. VSPs como tanto um separado por vírgulas ou um arquivo XML. Você pode filtrar os dados na janela de exibição do relatório antes de exportá\-la ou você pode exportar exibições de relatório do arquivo de dados inteiro do **Performance Explorer** janela.  
  
> [!NOTE]
>  Você também pode copiar e colar linhas selecionadas da janela de exibição do relatório como valores separada.  
  
#### Para exportar relatórios de desempenho da janela Performance Explorer  
  
1.  Em **Performance Explorer**, selecione o relatório e, em seguida, clique com botão direito e selecione **exportar**.  
  
     O **Exportar relatório** caixa de diálogo é exibida.  
  
2.  Selecione os modos de exibição de relatório que você deseja exportar.  
  
3.  Em **prefixo relatório com**, especifique o prefixo que você deseja adicionar ao nome do relatório.  
  
4.  Em **exportados local do relatório**, especifique o diretório.  
  
5.  Em **formato de relatório exportados**, selecione \(delimitado por vírgula\) \(\*. csv\), ou dados XML \(\*. xml\).  
  
6.  Clique em **exportar**.  
  
     Cada modo de exibição de relatório é salvo em um arquivo separado que é chamado \< prefixo \> \_ \< nome de exibição do relatório \>. \< csv &#124; xml \>  
  
#### Para exportar relatórios de desempenho na janela de exibição de relatório  
  
1.  Abra o arquivo. vsp na janela de exibição do relatório.  
  
2.  \(Opcional\) Aplica um filtro aos dados. Para obter mais informações, consulte [Filtro de exibição do relatório de ferramentas de criação de perfil](../profiling/performance-report-view-filter.md).  
  
3.  Clique em **Exportar relatório** na barra de ferramentas de janela de exibição relatório.  
  
4.  Selecione os modos de exibição de relatório que você deseja exportar.  
  
5.  Em **prefixo relatório com**, especifique o prefixo que você deseja adicionar ao nome do relatório.  
  
6.  Em **exportados local do relatório**, especifique o diretório.  
  
7.  Em **formato de relatório exportados**, selecione \(delimitado por vírgula\) \(\*. csv\), ou dados XML \(\*. xml\).  
  
8.  Clique em **exportar**.  
  
     Cada modo de exibição de relatório é salvo em um arquivo separado que é chamado \< prefixo \> \_ \< nome de exibição do relatório \>. \< csv &#124; xml \>  
  
## Consulte também  
 [Performance Explorer](../profiling/performance-explorer.md)   
 [Dados de ferramentas de análise de desempenho](../profiling/analyzing-performance-tools-data.md)   
 [Comparando arquivos de dados de desempenho](../profiling/comparing-performance-data-files.md)   
 [VSPerfReport](../profiling/vsperfreport.md)