---
title: "Como: adicionar consultas globais a um TableAdapter | Microsoft Docs"
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
  - "funções globais, conjuntos de dados"
  - "funções escalares, conjuntos de dados"
  - "TableAdapters, consultas globais"
  - "dados [Visual Studio], TableAdapters"
  - "conjuntos de dados [Visual Basic], funções escalares"
  - "TableAdapter Assistente de Configuração de Consulta"
  - "conjuntos de dados [Visual Basic], funções globais"
  - "consultas TableAdapter"
  - "consultas [Visual Studio], TableAdapters"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como: adicionar consultas globais a um TableAdapter
*Global queries* são consultas SQL que retornam um valor único \(escalar\) ou nenhum valor.  Normalmente, funções globais executam operações de banco de dados como inserir, atualizar, excluir e agregar informação, como retornar uma contagem dos clientes em uma tabela ou o total de cobranças para todos os itens em uma ordem específica.  
  
 Você adiciona consultas globais, executando o **TableAdapter Query Configuration Wizard** dentro do  **DataSet Designer** .  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para adicionar uma consulta global a um DataSet  
  
1.  Abra um dataset no **Dataset Designer**.  Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Arraste um **Query**  a partir da guia **DataSet** do **ToolBox** para uma área vazia do  **DataSet Designer**.  
  
     The [Editando TableAdapters](../data-tools/editing-tableadapters.md) opens.  
  
3.  Escolha uma conexão para a consulta a ser usada.  Você pode escolher uma a partir da lista ou criar uma nova conexão.  Se você criar uma nova conexão, você terá a opção de salvá\-la no arquivo de configuração do aplicativo.  Para obter mais informações, consulte [Como salvar e editar cadeias de conexão](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md).  
  
4.  Escolha se deseja usar procedimentos armazenados ou instruções SQL.  
  
5.  Escolha o procedimento armazenado a usar ou, na página **Choose a Query Type** do assistente, escolha o tipo de consulta você deseja e, em seguida, clique em **Next**.  
  
6.  Fornece uma consulta que realiza a tarefa desejada, por exemplo, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  Arrastar uma consulta diretamente para a **DataSet Designer** cria um método que só retornará um valor escalar \(único\).  Enquanto a consulta ou procedimento armazenado que você selecionar pode retornar mais de um único valor, o método criado pelo assistente só retorna um valor único.  Por exemplo, a consulta pode retornar a primeira coluna da primeira linha dos dados retornados.  
  
7.  Conclua o assistente; a consulta é adicionada ao **DataSet Designer**.  Para obter informações sobre a execução da consulta, consulte [Como executar consultas TableAdapter](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md).  
  
## Consulte também  
 [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)   
 [Como criar consultas TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)   
 [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)   
 [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Como navegar em dados com o controle BindingNavigator dos Windows Forms](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)