---
title: "Exibir dados relacionados em aplicativos WPF | Microsoft Docs"
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
  - "dados [WPF], exibindo"
  - "WPF, ligação de dados no Visual Studio"
  - "associação de dados WPF [Visual Studio]"
  - "exibindo dados de WPF"
  - "WPF [WPF], dados"
  - "Designer de WPF, associação de dados"
  - "associação de dados, WPF"
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Exibir dados relacionados em aplicativos WPF
Em alguns aplicativos, convém trabalhar com dados provenientes de várias tabelas ou entidades que estão relacionadas uns aos outros em uma relação pai\-filho. Por exemplo, você talvez queira exibir uma grade que exibe clientes de um `Customers` tabela. Quando o usuário seleciona um cliente específico, outra grade exibe os pedidos desse cliente de um relacionados `Orders` tabela.  
  
 Você pode criar controles ligados a dados que exibem dados relacionados, arrastando itens do **fontes de dados** janela para o WPF Designer.  
  
## Para criar controles que exibem registros relacionados  
  
1.  Sobre o **dados** menu, clique em **Show Data Sources** para abrir o **fontes de dados** janela.  
  
2.  Clique em **Add New Data Source** e conclua o **Data Source Configuration Wizard**.  
  
3.  Abra o designer WPF e certifique\-se de que o designer contém um contêiner é um destino válido para os itens do **fontes de dados** janela.  
  
     Para obter mais informações sobre destinos depósitos válidos, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  No **fontes de dados** janela, expanda o nó que representa a tabela pai ou do objeto da relação. A tabela pai ou o objeto está no lado "um" de uma relação um\-para\-muitos.  
  
5.  Arraste o nó pai \(ou todos os itens individuais no nó pai\) do **fontes de dados** janela para um destino válido no designer.  
  
     O Visual Studio gera XAML que cria novos controles ligados a dados para cada item que você arrasta. O XAML também adiciona um novo <xref:System.Windows.Data.CollectionViewSource> para a tabela pai ou objeto para os recursos de destino de soltar. Para algumas fontes de dados, o Visual Studio também gera código para carregar os dados na tabela pai ou objeto. Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  No **fontes de dados** janela, localize a tabela filho relacionada ou o objeto. Objetos e tabelas filho relacionadas aparecem como nós expansíveis na parte inferior da lista do nó pai de dados.  
  
7.  Arraste o nó filho \(ou todos os itens individuais no nó filho\) do **fontes de dados** janela para um destino válido no designer.  
  
     O Visual Studio gera XAML que cria novos controles ligados a dados para cada um dos itens que você arrasta. O XAML também adiciona um novo <xref:System.Windows.Data.CollectionViewSource> para a tabela filho ou o objeto para os recursos de destino de soltar. Esse novo <xref:System.Windows.Data.CollectionViewSource> está associado à propriedade da tabela pai ou do objeto que você acabou de arrastar para o designer. Para algumas fontes de dados, o Visual Studio também gera código para carregar os dados na tabela filho ou objeto.  
  
     A figura a seguir demonstra o relacionado **pedidos** índice da **clientes** tabela em um conjunto de dados a **fontes de dados** janela.  
  
     ![Relação de exibição de janela de fontes de dados](~/data-tools/media/datasources2.gif "DataSources2")  
  
## Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Criar tabelas de pesquisa em aplicativos do WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Instruções passo a passo: exibindo dados relacionados em um aplicativo WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)