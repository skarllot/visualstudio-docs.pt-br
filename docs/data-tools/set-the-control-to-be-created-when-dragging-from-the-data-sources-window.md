---
title: "Como definir o controle a ser criado quando arrastado da janela Fontes de Dados | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "dados [Visual Studio], janela Fontes de Dados"
  - "dados [Visual Studio], exibindo em Windows Forms"
  - "Janela Fontes de Dados, selecionar controles"
  - "Windows Forms, exibindo dados"
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 31
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como definir o controle a ser criado quando arrastado da janela Fontes de Dados
Você pode criar controles associados a dados arrastando itens do **fontes de dados** janela no designer do Windows Forms ou WPF designer. Cada item de **fontes de dados** janela tem um controle padrão que é criado quando você arrastá\-lo para o designer. No entanto, você pode optar por criar um controle diferente.  
  
## Configurando os controles a serem criados para tabelas de dados ou objetos  
 Antes de arrastar itens que representam as tabelas de dados ou objetos a partir de **fontes de dados** janela, você pode optar por exibir todos os dados em um controle ou para exibir cada coluna ou propriedade em um controle separado.  
  
 Nesse contexto, o termo *objeto* refere\-se a um objeto comercial personalizado, uma entidade \(em um modelo de dados de entidade\) ou um objeto retornado por um serviço.  
  
#### Para definir os controles a serem criados para tabelas de dados ou objetos  
  
1.  Certifique\-se de que o WPF designer ou o designer de formulários do Windows é aberto.  
  
2.  No **fontes de dados** janela, selecione o item que representa a tabela de dados ou objeto que você deseja definir.  
  
3.  Clique no menu suspenso para o item e, em seguida, clique em um dos seguintes itens no menu:  
  
    -   Para exibir cada campo de dados em um controle separado, clique em **detalhes**. Quando você arrasta o item de dados para o designer, essa ação criará um controle ligado a dados diferente para cada coluna ou propriedade do objeto, juntamente com os rótulos para cada controle ou tabela de dados pai.  
  
    -   Para exibir todos os dados em um único controle, selecione um controle diferente na lista, como **DataGrid** ou **lista** em um aplicativo WPF, ou **DataGridView** em um aplicativo Windows Forms.  
  
     A lista de controles disponíveis depende em qual designer tiver aberto, qual versão do .NET Framework seus destinos de projeto, e se você adicionou personalizado que suporte a vinculação de dados para os controles de **Toolbox**. Se o controle que você deseja criar na lista de controles disponíveis, você pode adicionar o controle à lista. Para obter mais informações, consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Para saber como criar um controle personalizado do Windows Forms que pode ser adicionado à lista de controles para tabelas de dados ou objetos no **fontes de dados** janela, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).  
  
## Configurando os controles a serem criados para colunas de dados ou propriedades  
 Antes de arrastar um item que representa uma coluna ou uma propriedade de um objeto a partir de **fontes de dados** janela no Designer, você pode definir o controle a ser criado.  
  
#### Para definir os controles a serem criados para colunas ou propriedades  
  
1.  Certifique\-se de que o WPF designer ou o designer de formulários do Windows é aberto.  
  
2.  No **fontes de dados** janela, expanda a tabela desejada ou objeto para exibir suas colunas ou propriedades.  
  
3.  Selecione cada coluna ou propriedade para o qual você deseja definir o controle a ser criado.  
  
4.  Clique no menu suspenso para a coluna ou propriedade e, em seguida, selecione o controle que você deseja criar quando o item é arrastado para o designer.  
  
     A lista de controles disponíveis depende em qual designer tiver aberto, qual versão do .NET Framework seus destinos de projeto e qual personalizar controles que suportam dados que você adicionou ao **Toolbox**. Se o controle que você deseja criar na lista de controles disponíveis, você pode adicionar o controle à lista. Para obter mais informações, consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
     Para saber como criar um controle personalizado que pode ser adicionado à lista de controles para colunas de dados ou propriedades de **fontes de dados** janela, consulte [Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).  
  
     Selecione **nenhum** no menu suspenso, se você não quiser criar um controle para a coluna ou propriedade. Isso é útil se você deseja arrastar a tabela pai ou o objeto para o designer, mas você não deseja incluir a coluna ou propriedade específica.  
  
## Consulte também  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)