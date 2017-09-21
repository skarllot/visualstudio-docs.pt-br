---
title: "Associar controles dos Windows Forms a dados no Visual Studio | Microsoft Docs"
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
  - "dados [Windows Forms], fontes de dados"
  - "Formulários do Windows, associação de dados"
  - "Windows Forms, exibindo dados"
  - "exibindo dados em formulários"
  - "formulários, exibindo dados"
  - "fontes de dados, exibindo dados"
  - "exibindo dados de Windows Forms"
  - "dados [Windows Forms], exibindo"
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
caps.latest.revision: 37
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associar controles dos Windows Forms a dados no Visual Studio
Você pode exibir dados para usuários do seu aplicativo pela vinculação de dados para formulários do Windows. Para criar esses controles ligados a dados, você pode arrastar itens do **fontes de dados** janela para o Windows Forms Designer no Visual Studio. Este tópico descreve algumas das tarefas, ferramentas e classes envolvidas na criação de aplicativos do Windows Forms associado a dados mais comuns.  
  
 ![Data Source drag operation](~/data-tools/media/raddata-data-source-drag-operation.png "raddata Data Source drag operation")  
  
 Para obter informações gerais sobre como criar controles ligados a dados no Visual Studio, consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obter mais informações sobre associação de dados no Windows Forms, consulte [Associação de dados do Windows Forms](../Topic/Windows%20Forms%20Data%20Binding.md).  
  
## Nesta seção  
  
-   [Vincular controles Windows Forms a dados](../data-tools/bind-windows-forms-controls-to-data.md)  
  
-   [Confirmar edições em processo em controles ligados a dados antes de salvar dados](../data-tools/commit-in-process-edits-on-data-bound-controls-before-saving-data.md)  
  
-   [Criar tabelas de pesquisa em aplicativos do Windows Forms](../data-tools/create-lookup-tables-in-windows-forms-applications.md)  
  
-   [Criar um Windows Form para pesquisar dados](../data-tools/create-a-windows-form-to-search-data.md)  
  
-   [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)  
  
-   [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)  
  
-   [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)  
  
-   [Passar dados entre formulários](../data-tools/pass-data-between-forms.md)  
  
## Componente BindingSource  
 O <xref:System.Windows.Forms.BindingSource> componente serve a dois propósitos. Primeiro, ele fornece uma camada de abstração ao associar os controles no formulário de dados. Controles no formulário são vinculados para o <xref:System.Windows.Forms.BindingSource> componente \(em vez de sendo vinculados diretamente a uma fonte de dados\).  
  
 Em segundo lugar, ele pode gerenciar uma coleção de objetos. Adicionando um tipo para o <xref:System.Windows.Forms.BindingSource> cria uma lista desse tipo.  
  
 Para obter mais informações sobre o <xref:System.Windows.Forms.BindingSource> componente, consulte:  
  
-   [Componente BindingSource](../Topic/BindingSource%20Component.md)  
  
-   [Visão geral do componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
-   [Arquitetura do componente BindingSource](../Topic/BindingSource%20Component%20Architecture.md)  
  
## Controle BindingNavigator  
 Esse componente fornece uma interface de usuário para navegar pelos dados exibidos por um aplicativo do Windows. Para obter mais informações, consulte [Controle BindingNavigator](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md).  
  
## Controle DataGridView  
 O <xref:System.Windows.Forms.DataGridView> control permite exibir e editar dados tabulares de muitos tipos diferentes de fontes de dados. Você pode associar dados a um <xref:System.Windows.Forms.DataGridView> usando o <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade. Para obter mais informações, consulte [Visão geral do controle DataGridView](../Topic/DataGridView%20Control%20Overview%20\(Windows%20Forms\).md).  
  
## Consulte também  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)