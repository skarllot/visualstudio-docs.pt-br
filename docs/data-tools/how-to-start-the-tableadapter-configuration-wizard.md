---
title: "Como iniciar o assistente de configura&#231;&#227;o TableAdapter | Microsoft Docs"
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
  - "TableAdapter Assistente de Configuração"
  - "TableAdapters, Assistente de Configuração"
ms.assetid: 301f2dcd-ed72-4229-80ef-3b59cb062d5d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como iniciar o assistente de configura&#231;&#227;o TableAdapter
O **Assistente de configuração TableAdapter** cria e edita TableAdapters em datasets fortemente tipados. O assistente cria TableAdapters baseados em instruções SQL que você insere no assistente ou em procedimentos armazenados no banco de dados existente. O assistente também pode criar novos procedimentos armazenados no banco de dados com base em instruções SQL inseridas no assistente.  
  
### Para iniciar o Assistente de configuração do TableAdapter para criar um novo TableAdapter  
  
1.  Abra o dataset no **Dataset Designer**. Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
    > [!NOTE]
    >  Se você não tiver um conjunto de dados em seu projeto, consulte [Criar e configurar conjuntos de dados](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
2.  Se você estiver criando um novo TableAdapter, arraste um **TableAdapter** de objeto o **DataSet** guia do **Toolbox** até o **Dataset Designer**.  
  
3.  Sobre o **Choose Your Data Connection** página, selecione uma conexão de dados da lista de conexões atualmente disponíveis ou selecione **nova conexão** para criar uma nova conexão.  
  
### Para iniciar o Assistente de configuração do TableAdapter para editar um TableAdapter existente  
  
1.  Abra o dataset no **Dataset Designer**. Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Clique com botão direito no TableAdapter no **Dataset Designer** e escolha **Configurar**. O assistente abre o **gerar as instruções SQL** página ou o **ligar comandos aos procedimentos armazenados existentes** página, dependendo de como o TableAdapter foi originalmente configurado.  
  
3.  Conclua o assistente.  
  
## Consulte também  
 [Instruções passo a passo de dados](../Topic/Data%20Walkthroughs.md)   
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)   
 [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)   
 [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Como classificar e filtrar dados ADO.NET com o componente BindingSource dos Windows Forms](../Topic/How%20to:%20Sort%20and%20Filter%20ADO.NET%20Data%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Como criar uma tabela de pesquisa com o componente BindingSource dos Windows Forms](../Topic/How%20to:%20Create%20a%20Lookup%20Table%20with%20the%20Windows%20Forms%20BindingSource%20Component.md)   
 [Instruções passo a passo: exibindo dados em um Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)