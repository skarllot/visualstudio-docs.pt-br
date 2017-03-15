---
title: "Criando e editando conjuntos de dados tipados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner"
  - "vs.data.adddataset"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
  - "aspx"
helpviewer_keywords: 
  - "dados [Visual Studio], Designer de Conjunto de Dados"
  - "Designer de Conjunto de Dados"
  - "conjuntos de dados [Visual Basic], designer visual"
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Criando e editando conjuntos de dados tipados
**Dataset Designer** É um conjunto de ferramentas visuais que você pode usar para criar e editar os datasets tipados e itens individuais que contêm.  
  
 O **DataSet Designer** fornece representações visuais dos objetos contidos em datasets tipados.  Você cria e modifica [TableAdapters](../data-tools/tableadapter-overview.md), [TableAdapter Queries](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s e <xref:System.Data.DataRelation>s com o **Designer de Conjunto de Dados**.  
  
 Para abrir o **DataSet Designer**, clique duas vezes em um conjunto de dados no **Solution Explorer**, ou clique com o botão direito do mouse em um conjunto de dados na janela **Data Sources** e clique em **Edit DataSet with Designer**.  Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  Adicionar um novo item <xref:System.Data.DataSet> com a caixa de diálogo **Add New Item** abrirá o **Dataset Designer** com um dataset vazio pronto para edição.  
  
> [!NOTE]
>  O **Dataset Designer** pode ser usado para estender a funcionalidade de um dataset.  Clique duas vezes na superfície de design ou clique com o botão direito do mouse e escolha **View Code** para criar um arquivo de classe parcial onde é possível adicionar código ao conjunto de dados que não será alterado ou excluído pelo designer.  Para obter informações sobre estender a funcionalidade de um TableAdapter, consulte [Estender a funcionalidade de um TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 A tabela a seguir lista as tarefas comuns que podem ser realizadas com o **DataSet Designer**.  
  
|Para|Consulte|  
|----------|--------------|  
|Criar um TableAdapter|[Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|  
|Editar um TableAdapter|[Como editar TableAdapters](../Topic/How%20to:%20Edit%20TableAdapters.md)|  
|Criar uma consulta do TableAdapter|[Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Editar uma consulta do TableAdapter|[Como editar consultas TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Criar um <xref:System.Data.DataTable>.|[Como criar tabelas de dados](../data-tools/how-to-create-data-tables.md)|  
|Editar um <xref:System.Data.DataTable>|[Criando DataTables](../data-tools/designing-datatables.md)|  
|Criar um <xref:System.Data.DataColumn>.|[Como adicionar colunas a um DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md)|  
|Criar uma relação entre duas <xref:System.Data.DataTable> s|[Como criar DataRelations com o Designer de Conjunto de Dados](../Topic/How%20to:%20Create%20DataRelations%20with%20the%20Dataset%20Designer.md)|  
|Estender a funcionalidade do conjunto de dados|[Como estender a funcionalidade de um conjunto de dados](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)|  
|Adicionar validação a um evento <xref:System.Data.DataTable.ColumnChanging> de uma tabela de dados|[Como validar dados durante alterações em coluna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md)|  
|Adicionar validação a um evento <xref:System.Data.DataTable.RowChanging> de uma tabela de dados|[Como validar dados durante alterações de linha](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md)|  
  
## Criando objetos sobre a superfície de design  
 Você pode criar conjuntos de dados adicionando e editando os objetos individuais que compõem um dataset.  A tabela a seguir fornece uma explicação sobre os diferentes objetos na guia **DataSet** da **ToolBox** que podem ser arrastados para a superfície de design:  
  
|Object|Descrição|  
|------------|---------------|  
|TableAdapter|Contém uma coleção de comandos de dados e um conexão de dados que são usados para comunicação com o banco de dados subjacente e preencher um tabela de dados.  Para obter mais informações, consulte [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md) e [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).|  
|Consulta|Consultas do TableAdapter são métodos fortemente tipados que executam instruções SQL e procedimentos armazenados.  Executar uma consulta do TableAdapter preenche um tabela de dados com dados ou executa outras tarefas de banco de dados.  Para obter mais informações, consulte [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  Arrastar uma consulta para uma tabela adiciona a consulta à tabela, enquanto arrastar uma consulta para uma área vazia do **Dataset Designer** cria uma consulta global.  Para obter mais informações, consulte [Como: adicionar consultas globais a um TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Representa uma coleção em memória das linhas retornadas de um banco de dados.|  
|Relação \(<xref:System.Data.DataRelation>\)|Representa um relacionamento pai\-filho entre dois <xref:System.Data.DataTable>S.  Para obter mais informações, consulte [Introdução a objetos DataRelation](../Topic/Introduction%20to%20DataRelation%20Objects.md) e [Instruções passo a passo: criando um relacionamento entre tabelas de dados](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md).|  
  
> [!NOTE]
>  **Dataset Designer** Se conecta a um base de dados subjacente somente quando um dataset é criado; o designer não detecta automaticamente alterações subsequentes a base de dados.  Para atualizar um .xsd existente, execute novamente **Assistente de Configuração**.  Se as relações de tabela mudaram, remover e re\-adicionar as tabelas relevantes para o .xsd.  
  
## LINQ to Dataset  
 [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] habilita [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) sobre os dados em um objeto <xref:System.Data.DataSet>.  Para obter mais informações, consulte [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
## Consulte também  
 [Instruções passo a passo: criando um conjunto de dados com o Designer de Conjunto de Dados](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Instruções passo a passo: criando um TableAdapter com várias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Instruções passo a passo: criando um DataTable no Designer de Conjunto de Dados](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Instruções passo a passo: criando um relacionamento entre tabelas de dados](../Topic/Walkthrough:%20Creating%20a%20Relationship%20between%20Data%20Tables.md)   
 [Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md)   
 [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)