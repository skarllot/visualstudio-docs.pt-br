---
title: "Conjuntos de dados separados e TableAdapters em diferentes projetos | Microsoft Docs"
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
  - "TableAdapters, aplicativos de n camadas"
  - "aplicativos de n camadas, separando conjuntos de dados e TableAdapters"
ms.assetid: f66a3940-6227-46af-a930-9177f425f4fd
caps.latest.revision: 18
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conjuntos de dados separados e TableAdapters em diferentes projetos
Datasets tipados foram aprimorados de modo que [TableAdapters](../Topic/TableAdapters.md) e classes dataset possam ser gerados em projetos separados.  Isso permite que você separar camadas de aplicativo e para gerar rapidamente aplicativos de dados n\-tier.  
  
 O procedimento a seguir descreve o processo de usar [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md) para gerar código de dataset em um projeto que é separado do projeto que contém o código gerado de `TableAdapter` .  
  
## Separando dataset e TableAdapters  
 Quando você separar o código de dataset do código de `TableAdapter` , o projeto que conterá o código de dataset deve ser localizado na solução atual.  Se este projeto não está localizado na solução atual, não estará disponível na lista de **Projeto do Conjunto de Dados** na janela de **Propriedades** .  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para separar o dataset em um projeto diferente  
  
1.  Abra uma solução que contém um conjunto de dados \(arquivo.xsd\).  
  
    > [!NOTE]
    >  Se a solução não contém o projeto em que você deseja para separar o código do conjunto de dados, para o criar, ou para adicionar um projeto existente à solução.  
  
2.  Clique duas vezes em um arquivo tipado dataset \(um arquivo .xsd\) em **Gerenciador de Soluções** para abrir o dataset em **Dataset Designer**.  
  
3.  Clique em uma área vazia de **Dataset Designer**.  
  
4.  Localize o  **DataSet Project**  nó na janela de **Properties**.  
  
5.  Na lista de **Projeto do Conjunto de Dados** , clique no nome do projeto no qual você deseja gerar o código de dataset.  
  
     Após você clicar no projeto em que você deseja gerar o código de dataset, a propriedade de **Arquivo do Conjunto de Dados** é preenchida com um nome de arquivo padrão.  Você pode alterar esse nome se você precisa.  Além disso, se você desejar gerar o código de dataset em um diretório específico, você pode definir a propriedade de **Pasta do Projeto** o nome de uma pasta.  
  
    > [!NOTE]
    >  Quando você separar DataSets de TableAdapters \(configurando a propriedade **DataSet Project**\), classes parciais DataSet existentes no projeto não serão movidas automaticamente.  Classes parciais DataSet existente devem ser movidas manualmente para o projeto DataSet.  
  
6.  Salve o conjunto de dados.  
  
     O código de dataset é gerado no projeto selecionado na propriedade de **Projeto do Conjunto de Dados** , e o código de **TableAdapter** é gerado no projeto atual.  
  
 Por padrão, após você separar o DataSet e `TableAdapter` código, o resultado é um arquivo de classe distintas em cada projeto.  O projeto original tem um arquivo chamado DatasetName.Designer.vb \(ou DatasetName.Designer.cs\) que contém o código de `TableAdapter` .  O projeto designado na propriedade de **Dataset Project** tem um arquivo chamado DatasetName.DataSet.Designer.vb \(ou DatasetName.DataSet.Designer.cs\) que contém o código de dataset.  
  
> [!NOTE]
>  Com o conjunto de dados ou projeto de `TableAdapter` selecionado, clique **Mostrar todos os arquivos** em **Gerenciador de Soluções** para exibir o arquivo gerado de classe.  
  
## Consulte também  
 [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)   
 [Instruções passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Atualização hierárquica](../data-tools/hierarchical-update.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [ADO.NET](../Topic/ADO.NET.md)