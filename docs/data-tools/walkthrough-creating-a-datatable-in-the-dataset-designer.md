---
title: "Instru&#231;&#245;es passo a passo: criando um DataTable no Designer de Conjunto de Dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "dados [Visual Studio], Designer de Conjunto de Dados"
  - "Designer de Conjunto de Dados, criando tabelas de dados"
  - "Objetos DataTable, criando"
  - "tabelas [Visual Studio], criando"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Instru&#231;&#245;es passo a passo: criando um DataTable no Designer de Conjunto de Dados
Essa explicação passo a passo explica como criar uma <xref:System.Data.DataTable> \(sem um TableAdapter\) usando o **DataSet Designer**.  Para obter informações sobre como criar tabelas de dados que incluem TableAdapters, consulte [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
 As tarefas ilustradas neste passo a passo incluem:  
  
-   Criar um novo projeto de Windows Application  
  
-   Adicionar um novo dataset ao aplicativo  
  
-   Adicionar uma nova tabela de dados para o dataset  
  
-   Adicionar colunas à tabela de dados  
  
-   Definir a chave primária para a tabela  
  
## Criando um novo aplicativo Windows  
  
#### Para criar um novo projeto de Aplicativo do Windows  
  
1.  No menu **File**, crie um novo projeto.  
  
2.  Escolha uma linguagem de programação no painel **Project Types**.  
  
3.  Clique em **Windows Application** no painel **Templates**.  
  
4.  Nomeie o projeto `DataTableWalkthrough`, e clique **OK**.  
  
     O Visual Studio adiciona o projeto ao **Solution Explorer** e exibe o **Form1** no designer.  
  
## Adicionando um novo dataset ao aplicativo  
  
#### Para adicionar um novo item dataset para o projeto  
  
1.  No menu **Project**, clique em **Add New Item**.  
  
     A caixa de diálogo Add New Item Dialog Box aparece.  
  
2.  Na caixa **Templates**, selecione **DataSet**.  
  
3.  Clique em **Adicionar**.  
  
     O Visual Studio irá adicionar um arquivo chamado **DataSet1.xsd** ao projeto e o abrirá no **Dataset Designer**.  
  
## Adicionando um DataTable novo ao Dataset  
  
#### Para adicionar uma nova tabela de dados ao dataset  
  
1.  Arraste uma **DataTable** da guia **DataSet** do **Toolbox** para o **Dataset Designer**  
  
     Uma tabela denominada **DataTable1** é adicionada ao dataset.  
  
    > [!NOTE]
    >  Para criar um tabela de dados que inclui um TableAdapter, consulte [Instruções passo a passo: criando um TableAdapter com várias consultas](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Clique na barra de título do **DataTable1** e renomeie para `Music`.  
  
## Adicionando colunas à tabela de dados  
  
#### Para adicionar colunas à tabela de dados  
  
1.  Clique com o botão direito do mouse na tabela **Music**.  Aponte para **Add**, e clique **Column**.  
  
2.  Nome da coluna `SongID`.  
  
3.  No  **Propriedades** janela, defina a <xref:System.Data.DataColumn.DataType%2A> propriedade para <xref:System.Int16?displayProperty=fullName>.  
  
4.  Repita este processo e adicione as seguintes colunas:  
  
     `SongTitle` : <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## Definindo a chave primária para a tabela  
 Todas as tabelas de dados devem ter uma chave primária.  Uma chave primária identifica exclusivamente um registro específico em uma tabela de dados.  
  
#### Para definir a chave primária da tabela de dados  
  
-   Clique com o botão direito do mouse na coluna **SongID**, e clique **Set Primary Key**.  
  
     Um ícone de chave aparece próxima à coluna **SongID**.  
  
## Salvando seu projeto  
  
#### Para salvar o projeto DataTableWalkthrough  
  
-   No menu **File**, clique em **Save All**.  
  
## Próximas etapas  
 Agora que você criou a tabela, você pode desejar executar uma das seguintes ações:  
  
|Para|Consulte|  
|----------|--------------|  
|Criar um formulário para entrada de dados|[Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Adicionar dados à tabela|[Adicionando dados a um DataTable](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|Visualizar dados em uma tabela|[Exibindo dados em uma DataTable](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|Editar dados|[Edições de DataTable](../Topic/DataTable%20Edits.md)|  
|Excluir uma linha de uma tabela|[Exclusão de DataRow](../Topic/DataRow%20Deletion.md)|  
  
## Consulte também  
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)   
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)