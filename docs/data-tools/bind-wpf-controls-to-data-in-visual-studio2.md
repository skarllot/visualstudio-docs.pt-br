---
title: "Associar controles WPF a dados no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dados [WPF], exibindo"
  - "WPF, ligação de dados no Visual Studio"
  - "associação de dados WPF [Visual Studio]"
  - "exibindo dados de WPF"
  - "WPF [WPF], dados"
  - "Designer de WPF, associação de dados"
  - "associação de dados, WPF"
ms.assetid: 00dd5147-db0b-4b59-8d6c-8229b09ca9dd
caps.latest.revision: 26
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associar controles WPF a dados no Visual Studio
Você pode criar uma associação de dados [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] controles usando o **fontes de dados** janela. Primeiro, adicione uma fonte de dados para o **fontes de dados** janela. Em seguida, arraste itens do **fontes de dados** janela **o WPF Designer**.  
  
##  <a name="adding"></a> Adicionando uma fonte de dados à janela fontes de dados  
 Antes de criar controles ligados a dados, você deve primeiro adicionar uma fonte de dados para o **fontes de dados** janela.  
  
#### Para adicionar uma fonte de dados à janela fontes de dados  
  
1.  Sobre o **exibição** aponte para **outras janelas**, e, em seguida, clique em **fontes de dados**.  
  
2.  Clique em **Add New Data Source** e conclua o **Data Source Configuration Wizard**.  
  
3.  Execute uma das seguintes tarefas para criar controles ligados a dados:  
  
    -   [Criar um controle que está associado a um único campo de dados](#simple).  
  
    -   [Criar um controle que é associado a vários campos de dados](#complex).  
  
    -   [Criando um conjunto de controles que são associados a vários campos de dados](#details).  
  
    -   [Associando dados a controles existentes no designer de](#existing).  
  
##  <a name="simple"></a> Criando um controle que está associado a um único campo de dados  
 Depois de adicionar uma fonte de dados para o **fontes de dados** janela, você pode criar um novo controle ligado a dados que exibe um único campo de dados, como um <xref:System.Windows.Controls.ComboBox> ou <xref:System.Windows.Controls.TextBox>.  
  
#### Para criar um controle associado a um único campo de dados  
  
1.  No **fontes de dados** janela, expandir um item que representa uma tabela ou um objeto. Localize o item filho que representa a coluna ou propriedade que você deseja associar a. Para obter um exemplo visual, consulte [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md).  
  
2.  Opcionalmente, selecione o controle a ser criado. Cada item de **fontes de dados** janela tem um controle padrão que é criado quando você arrasta o item para o designer. O controle padrão depende do tipo de dados subjacente do item.  
  
     Para escolher um controle diferente, clique na seta suspensa ao lado do item e selecione um controle. Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
3.  Arraste o item para um contêiner válido no designer. Para obter mais informações sobre contêineres válidos, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria o novo controle ligado a dados e apropriadamente intitulado <xref:System.Windows.Controls.Label> no contêiner.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e código para associar o controle aos dados. Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="complex"></a> Criando um controle que está vinculado a vários campos de dados  
 Depois de adicionar uma fonte de dados para o **fontes de dados** janela, você pode criar um novo controle ligado a dados que exibe vários campos de dados, como um <xref:System.Windows.Controls.DataGrid> ou <xref:System.Windows.Controls.ListView>.  
  
#### Para criar um controle que é associado a vários campos de dados  
  
1.  No **fontes de dados** janela, selecione um item que representa uma tabela ou objeto. Para obter um exemplo visual, consulte [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md).  
  
2.  Opcionalmente, selecione o controle a ser criado. Por padrão, cada item de **fontes de dados** que representa uma tabela de dados ou objeto de janela é definida para criar um <xref:System.Windows.Controls.DataGrid> \(se o seu projeto é direcionado para o .NET Framework 4\) ou <xref:System.Windows.Controls.ListView> \(para versões anteriores do .NET Framework\).  
  
     Para selecionar um controle diferente, clique na seta suspensa ao lado do item e selecione um controle. Para obter mais informações, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    > [!NOTE]
    >  Se você não deseja exibir uma propriedade ou coluna específica, expanda o item para exibir seus filhos. Clique na seta suspensa ao lado da coluna ou propriedade que você não deseja exibir e, em seguida, clique em **nenhum**.  
  
3.  Arraste o item para um contêiner válido no designer, como um <xref:System.Windows.Controls.Grid>. Para obter mais informações sobre contêineres válidos, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria o novo controle ligado a dados no contêiner. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e código para associar o controle aos dados. Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="details"></a> Criar um conjunto de controles que são associados a vários campos de dados  
 Depois de adicionar uma fonte de dados para o **fontes de dados** janela, você pode vincular uma tabela de dados ou objeto para um conjunto de controles. Um controle diferente é criado para cada coluna ou propriedade na tabela ou objeto.  
  
#### Para criar um conjunto de controles que são associados a vários campos de dados  
  
1.  No **fontes de dados** janela, selecione um item que representa uma tabela ou objeto. Para obter um exemplo visual, consulte [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md).  
  
2.  Clique na seta suspensa ao lado do item e selecione **detalhes**.  
  
    > [!NOTE]
    >  Se você não deseja exibir uma propriedade ou coluna específica, expanda o item para exibir seus filhos. Clique na seta suspensa ao lado da coluna ou propriedade que você não deseja exibir e, em seguida, clique em **nenhum**.  
  
3.  Arraste o item para um contêiner válido no designer, como um <xref:System.Windows.Controls.Grid>. Para obter mais informações sobre contêineres válidos, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cria os novos controles ligados a dados no contêiner. Cada controle é vinculado a uma outra coluna ou propriedade e cada controle é acompanhado por um apropriadamente intitulado <xref:System.Windows.Controls.Label> controle. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e código para associar controles aos dados. Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
##  <a name="existing"></a> Associando dados a controles existentes no Designer  
 Depois de adicionar uma fonte de dados para o **fontes de dados** janela, você pode adicionar um associação de dados a um controle existente no Designer.  
  
#### Para associar dados a um controle existente no designer  
  
1.  No **fontes de dados** janela, use um dos seguintes procedimentos:  
  
    -   Para adicionar uma associação de dados a um controle existente que exibe vários campos de dados, como um <xref:System.Windows.Controls.DataGrid> ou <xref:System.Windows.Controls.ListView>, selecione o item que representa a tabela ou objeto que você deseja associar ao controle.  
  
    -   Para adicionar uma associação de dados a um controle existente que exibe um único campo de dados, como um <xref:System.Windows.Controls.ComboBox> ou <xref:System.Windows.Controls.TextBox>, expanda o item que representa a tabela ou objeto que contém os dados e, em seguida, selecione o item que representa os dados que você deseja associar ao controle.  
  
2.  Arraste o item selecionado do **fontes de dados** janela para um controle existente no designer. O controle deve ser um destino válido. Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e código para associar o controle aos dados. Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
    > [!NOTE]
    >  Se o controle já está ligado a dados, a ligação de dados para o controle é redefinida para o item que foi arrastado para o controle mais recentemente.  
  
## Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Criar tabelas de pesquisa em aplicativos do WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Exibir dados relacionados em aplicativos WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Associar controles WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Associar controles WPF a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Instruções passo a passo: exibindo dados relacionados em um aplicativo WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)