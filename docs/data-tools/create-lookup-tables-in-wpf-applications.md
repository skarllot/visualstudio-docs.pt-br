---
title: "Criar tabelas de pesquisa em aplicativos do WPF | Microsoft Docs"
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Criar tabelas de pesquisa em aplicativos do WPF
Você pode criar uma tabela de pesquisa arrastando o nó principal de uma tabela pai ou objeto de **fontes de dados** janela em um controle que já esteja associado a uma coluna ou propriedade em uma tabela filho relacionada. O termo *tabela de pesquisa* \(às vezes chamado de um *vinculação de pesquisa*\) descreve um controle que exibe informações de uma tabela de dados com base no valor de um campo de chave estrangeira em outra tabela.  
  
 Por exemplo, considere uma tabela de `Orders` em um banco de dados de venda. Cada registro de `Orders` tabela inclui um `CustomerID` que indica qual cliente fez o pedido. O `CustomerID` é uma chave estrangeira que aponta para um registro de cliente no `Customers` tabela. Quando você exibe uma lista de pedidos do `Orders` tabela, você talvez queira exibir o nome real do cliente em vez do `CustomerID`. Porque o nome do cliente está no `Customers` tabela, você precisa criar uma tabela de pesquisa para exibir o nome do cliente. Os usos da tabela de pesquisa a `CustomerID` valor o `Orders` registro para navegar pelo relacionamento e retornar o nome amigável do cliente.  
  
## Para criar uma tabela de pesquisa  
  
1.  Adicione um dos seguintes tipos de fontes de dados com dados relacionados ao seu projeto:  
  
    -   Conjunto de dados ou modelo de dados de entidade. Para obter mais informações, consulte [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
    -   WCF Data Service, serviço WCF ou serviço da Web. Para obter mais informações, consulte [Como conectar a dados em um serviço](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
    -   Objetos. Para obter mais informações, consulte [Como conectar a dados em objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
    > [!NOTE]
    >  Antes de criar uma tabela de pesquisa, duas tabelas relacionadas ou objetos devem existir como uma fonte de dados para o projeto.  
  
2.  Abra **o WPF Designer** e certifique\-se de que o designer contém um contêiner é um destino válido para itens no **fontes de dados** janela.  
  
     Para obter mais informações sobre destinos depósitos válidos, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
3.  Sobre o **dados** menu, clique em **Show Data Sources** para abrir o **fontes de dados** janela.  
  
4.  Expanda os nós a **fontes de dados** janela até que você possa ver a tabela pai ou objeto e a tabela filho relacionada ou objeto.  
  
    > [!NOTE]
    >  A tabela filho relacionada ou o objeto é o nó que aparece como um nó filho expansível na tabela pai ou o objeto.  
  
5.  Clique no menu suspenso para o nó filho e selecione **detalhes**.  
  
6.  Expanda o nó filho.  
  
7.  Sob o nó filho, clique no menu suspenso para o item que relaciona os dados pai e filho \(no exemplo acima, isso seria o **CustomerID** nó\). Selecione um dos seguintes tipos de controles que suportam associação de pesquisa:  
  
    -   **ComboBox**  
  
    -   **Caixa de listagem**  
  
    -   **ListView**  
  
        > [!NOTE]
        >  Se o **ListBox** ou **ListView** controle não aparecer na lista, você pode adicionar esses controles à lista. Para obter mais informações, veja [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
    -   Qualquer controle personalizado que deriva de <xref:System.Windows.Controls.Primitives.Selector>.  
  
        > [!NOTE]
        >  Para obter informações sobre como adicionar personalizado controles à lista de controles que você podem selecionar itens na **fontes de dados** janela, consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
8.  Arraste o nó filho do **fontes de dados** janela para um contêiner no WPF designer \(no exemplo acima, o nó filho seria o **pedidos** nó\).  
  
     O Visual Studio gera XAML que cria novos controles ligados a dados para cada um dos itens que você arrasta. O XAML também adiciona um novo <xref:System.Windows.Data.CollectionViewSource> para a tabela filho ou o objeto para os recursos de destino de soltar. Para algumas fontes de dados, o Visual Studio também gera código para carregar dados para a tabela ou objeto. Para obter mais informações, consulte [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
9. Arraste o nó pai do **fontes de dados** janela para o controle de associação de pesquisa que você criou anteriormente \(no exemplo acima, o nó pai seria o **clientes** nó\).  
  
     O Visual Studio define algumas propriedades do controle para configurar a associação de pesquisa. A tabela a seguir lista as propriedades que o Visual Studio modifica. Se necessário, você pode alterar essas propriedades no XAML ou de **propriedades** janela.  
  
    |Propriedade|Explicação da configuração|  
    |-----------------|--------------------------------|  
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Esta propriedade especifica a coleção ou associação que é usada para obter os dados que são exibidos no controle. Visual Studio define essa propriedade para o <xref:System.Windows.Data.CollectionViewSource> para os dados pai que você arrastou para o controle.|  
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Esta propriedade especifica o caminho do item de dados que é exibido no controle. Visual Studio define essa propriedade para a primeira coluna ou propriedade de dados pai, após a chave primária, que tem um tipo de dados de cadeia de caracteres.<br /><br /> Se você quiser exibir uma coluna diferente ou a propriedade dos dados pai, altere essa propriedade para o caminho de uma propriedade diferente.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio vincula essa propriedade como a coluna ou propriedade de dados filho que você arrastou para o designer. Essa é a chave estrangeira para os dados pai.|  
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio define essa propriedade para o caminho da coluna ou propriedade dos dados filho que é a chave estrangeira para os dados pai.|  
  
## Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Exibir dados relacionados em aplicativos WPF](../data-tools/display-related-data-in-wpf-applications.md)   
 [Instruções passo a passo: exibindo dados relacionados em um aplicativo WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)