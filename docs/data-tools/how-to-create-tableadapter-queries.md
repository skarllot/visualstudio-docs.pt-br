---
title: "Como criar consultas TableAdapter | Microsoft Docs"
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
  - "dados [Visual Studio], consultas TableAdapter"
  - "consultas [Visual Studio], criando"
  - "consultas [Visual Studio], TableAdapters"
  - "TableAdapters, criando consultas"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como criar consultas TableAdapter
Consultas TableAdapter são instruções SQL ou procedimentos armazenados que seu aplicativo pode executar em um banco de dados.  
  
 Adiciona tantas consultas para um TableAdapter quanto seu aplicativo requer.  Consultas TableAdapter aparecem como métodos em um TableAdapter.  When you create a query called `FillByCity` that takes a parameter representing the city value, the query is added to the TableAdapter.  Ela é adicionada como um método digitado que leva o tipo correto do parâmetro como um argumento — no caso uma sequência representando o valor de cidade.  Você chama a consulta TableAdapter assim como qualquer método em qualquer objeto.  For example, the following code executes the `FillByCity` query and fills the `Customers` table with all customers with a city value of `Seattle`:  
  
 [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
 TableAdapter queries can fill a data table \(`Fill` and `FillBy` queries\) or return new data tables populated with the data returned by the query \(`GetData` and `GetDataBy` queries\).  
  
 You can add queries to existing TableAdapters by running the [Editando TableAdapters](../data-tools/editing-tableadapters.md).  \(Clique com o botão direito do mouse em qualquer TableAdapter e escolha **Add Query**.\)  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Criar uma consulta no DataSet Designer  
  
#### Para adicionar uma consulta a um TableAdapter no DataSet Designer  
  
1.  Abra um dataset no **Dataset Designer**.  Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Clique com o botão direito do mouse no TableAdapter desejado e selecione **Add Query**.  
  
     \- ou \-  
  
3.  Arraste um **Query** da tabela **DataSet** da **Toolbox** em uma tabela no designer.  
  
     O **TableAdapter Query Configuration Wizard** abre.  
  
4.  Conclua o assistente; a consulta é adicionada ao TableAdapter.  
  
## Criar uma Consulta Diretamente em um Formulário no seu Aplicativo Windows  
 If you have an instance of a TableAdapter on your form you can add a query using the [Caixa de diálogo Pesquisar Construtor de Critérios](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md), which adds a <xref:System.Windows.Forms.ToolStrip> control to the form that accepts any input parameters required by the query, as well as a button to run the query.  
  
#### Para adicionar uma consulta a um TableAdapter usando a caixa de diálogo critérios de pesquisa  
  
1.  Selecione um TableAdapter na bandeja do componente.  
  
2.  Clique na marca inteligente do TableAdapter e escolha **Add Query**.  
  
3.  Complete a caixa de diálogo e a consulta será adicionada ao TableAdapter.  Para obter mais informações, consulte [Caixa de diálogo Pesquisar Construtor de Critérios](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md).  
  
## Consulte também  
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Como editar consultas TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)   
 [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)   
 [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Como navegar em dados com o controle BindingNavigator dos Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Instruções passo a passo: criando um TableAdapter com várias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)