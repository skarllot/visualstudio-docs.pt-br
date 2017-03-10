---
title: "Como criar tabelas de dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VSDesigner.DataSource.DesignTable"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dados [Visual Studio], criando tabelas de dados"
  - "Designer de Conjunto de Dados, criando tabelas de dados"
  - "tabelas [Visual Studio], criando"
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como criar tabelas de dados
Dados podem ser armazenados na memória em <xref:System.Data.DataTable> objetos. \(Datasets são compostos de <xref:System.Data.DataTable> objetos.\) Você normalmente cria novas tabelas de dados com TableAdapters usando o [TableAdapter Assistente de Configuração](../Topic/TableAdapter%20Configuration%20Wizard.md) ou arrastando objetos de banco de dados de **Server Explorer** até o **Dataset Designer**.  
  
 Tabelas de dados são criadas como um subproduto quando você cria novos TableAdapters na [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png) mas também podem ser criadas independentemente. Você cria uma tabela de dados autônoma arrastando um <xref:System.Data.DataTable> de objeto o **DataSet** guia do **ferramentas** até o **Dataset Designer**.  
  
> [!NOTE]
>  Para criar tabelas de dados programaticamente, consulte [Criando uma DataTable](../Topic/Creating%20a%20DataTable.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Criando um DataTable com TableAdapter  
 Tabelas de dados com TableAdapters incluem métodos que preencha a tabela com dados e gravam alterações de volta para o banco de dados. Crie TableAdapters executando o **TableAdapter Configuration Wizard** ou arrastando objetos de banco de dados de **Server Explorer** até o **Dataset Designer**.  
  
#### Para criar uma nova tabela de dados com TableAdapter  
  
1.  Abra o dataset no **Dataset Designer**. Para obter mais informações, veja [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Arraste um **TableAdapter** do **DataSet** guia do **Toolbox** para o **Dataset Designer**.  
  
     O **Assistente de configuração TableAdapter** abre.  
  
3.  Conclua o assistente. Para obter mais informações, consulte [TableAdapter Assistente de Configuração](../Topic/TableAdapter%20Configuration%20Wizard.md).  
  
#### Para criar uma nova tabela de dados com um TableAdapter no Gerenciador de servidores  
  
1.  Abra o dataset no **Designer da fonte de dados**.  
  
2.  Arraste um objeto de banco de dados \(por exemplo, uma tabela\) da **Server Explorer** até o **Dataset Designer**.  
  
## Criando uma DataTable autônoma  
 Tabelas autônomas precisam ter `Fill` lógica implementada para ser preenchida com dados. Para obter informações sobre preenchimento de tabelas de dados autônoma, consulte [Populando um DataSet a partir de um DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
#### Para criar uma nova tabela de dados autônoma  
  
1.  Abra o dataset no **Dataset Designer**.  
  
2.  Arraste um <xref:System.Data.DataTable> do **DataSet** guia do **Toolbox** para o **Dataset Designer**.  
  
3.  Adicione colunas para definir sua tabela de dados. Para obter mais informações, consulte [Como adicionar colunas a um DataTable](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md).  
  
## Consulte também  
 <xref:System.Data.DataTable>   
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)   
 [Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)   
 [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)   
 [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md)   
 [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validando dados](../Topic/Validating%20Data.md)