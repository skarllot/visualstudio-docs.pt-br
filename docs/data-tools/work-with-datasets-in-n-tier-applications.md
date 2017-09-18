---
title: "Trabalhar com conjuntos de dados em aplicativos de n camadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
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
  - "conjuntos de dados [Visual Basic], aplicativos de n camadas"
  - "aplicativos de banco de dados de várias camadas"
  - "projeto DataSet [aplicativos de n camadas do VS]"
  - "aplicativos distribuídos [aplicativos de n camadas do VS]"
  - "dados [Visual Basic], aplicativos de n camadas"
  - "TableAdapters, aplicativos de n camadas"
  - "aplicativos de n camadas"
  - "camadas de aplicativos de n camadas"
  - "conjuntos de dados tipados, aplicativos de n camadas"
  - "aplicativos de várias camadas"
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Trabalhar com conjuntos de dados em aplicativos de n camadas
Os *aplicativos de dados de N camadas* são aplicativos centrados em dados que são separados em várias *camadas* lógicas camadas.  Em outras palavras, um aplicativo de dados de N camadas é um aplicativo separado em vários projetos, com camada de acesso a dados, camada lógica de negócios e camada de apresentação em seu próprio projeto.  Para obter mais informações, consulte [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md).  
  
 Os conjuntos de dados tipados foram aprimorados para que as classes TableAdapters e de conjuntos de dados possam ser geradas em projetos discretos.  Com isso, é possível separar com rapidez as camadas de aplicativos e gerar aplicativos de dados de N camadas.  
  
 O suporte a N camadas em conjuntos de dados tipados permite desenvolvimento iterativo da arquitetura do aplicativo para um design de N camadas e elimina a necessidade de separar manualmente o código em mais de um projeto.  Comece a projetar a camada de dados usando o [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md).  Quando você estiver pronto para aplicar a arquitetura do aplicativo a um projeto de N camadas, configure a propriedade **Projeto DataSet** de um conjunto de dados para gerar a classe do conjunto de dados em um projeto separado.  
  
## Nesta seção  
 [Conjuntos de dados separados e TableAdapters em diferentes projetos](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
 Descreve como mover a classe do conjunto de dados gerada para fora do projeto que contém as classes TableAdapter geradas e para dentro de um novo projeto.  
  
 [Adicionar código a TableAdapters em aplicativos de n camadas](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
 Descreve como gerar uma classe parcial na qual é possível adicionar código para um TableAdapter de N camadas.  
  
 [Adicionar código ao datasets em aplicativos de n camadas](../data-tools/add-code-to-datasets-in-n-tier-applications.md)  
 Descreve como gerar uma classe parcial na qual é possível adicionar código para um conjunto de dados de N camadas.  
  
 [Adicionar validação a um conjunto de dados de n camadas](../data-tools/add-validation-to-an-n-tier-dataset.md)  
 Descreve onde adicionar código para executar validação na alteração de dados.  
  
 [Instruções passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
 Fornece instruções passo a passo para criar um conjunto de dados tipado e separar o código do TableAdapter e do conjunto de dados em vários projetos.  
  
 [Instruções passo a passo: adicionando validação a um aplicativo de dados de N camadas](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)  
 Fornece instruções passo a passo para adicionar validação ao aplicativo criado no passo a passo do aplicativo de dados de N camadas.  
  
## Referência  
 <xref:System.Data.DataSet>  
  
 <xref:System.Data.TypedTableBase%601>  
  
## Seções relacionadas  
 [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)  
  
 [Atualização hierárquica](../data-tools/hierarchical-update.md)  
  
 [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)  
  
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)  
  
 [N\-Tier and Remote Applications with LINQ to SQL](../Topic/N-Tier%20and%20Remote%20Applications%20with%20LINQ%20to%20SQL.md)