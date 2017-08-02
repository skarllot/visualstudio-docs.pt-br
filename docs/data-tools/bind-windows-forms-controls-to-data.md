---
title: "Vincular controles Windows Forms a dados | Microsoft Docs"
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
  - "exibindo dados, controles de formulários do Windows"
  - "Windows Forms, exibindo dados"
  - "fontes de dados, exibindo"
  - "dados [Windows Forms], exibindo"
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 28
caps.handback.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vincular controles Windows Forms a dados
Você pode vincular fontes de dados a controles arrastando objetos a partir de  **janela fontes de dados** em um formulário do Windows ou em um controle existente em um formulário. Antes de arrastar itens, você pode definir o tipo de controle que você deseja associar a. Aparecem valores diferentes dependendo se você escolher a tabela em si, ou uma coluna individual.  Você também pode definir valores personalizados. Para uma tabela, "Detalhes" significa que cada coluna é associada a um controle separado.  
  
 ![Bind data source to DataGridView](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata Bind data source to DataGridView")  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Associando a dados em um controle DataGridView  
 Para DataGridView, a tabela inteira é vinculada ao controle único. Quando você arrasta um DataGridView ao formulário, uma faixa de ferramenta \(<xref:System.Windows.Forms.BindingNavigator>\) para navegação em registros também é exibido. Um [DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> aparecem na bandeja de componentes. Na ilustração a seguir, um TableAdapterManager também é adicionado porque a tabela clientes tem uma relação para a tabela Orders. Essas variáveis todos são declaradas no código gerado automaticamente como membros privados na classe de formulário. O código gerado automaticamente para preencher o DataGridView está localizado no manipulador de eventos form\_load e o código para salvar os dados para atualizar o banco de dados está localizado no manipulador de eventos de salvamento para o BindingNavigator. Você pode mover ou modificar esse código, conforme necessário.  
  
 ![GridView with BindingNavigator](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata GridView with BindingNavigator")  
  
 Você pode personalizar o comportamento do DataGridView e BindingNavigator clicando na marca inteligente no canto superior direito de cada um:  
  
 ![DataGridView and Binding Navigator smart tags](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView and Binding Navigator smart tags")  
  
 Se os controles necessitados para seu aplicativo não estão disponíveis no **fontes de dados** janela, você pode adicionar controles. Para obter mais informações, consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 Você também pode arrastar itens do **fontes de dados** window para controles já em um formulário para associar o controle aos dados. Um controle que já está ligado a dados tem seu associações a dados redefinidas para o item mais recentemente arrastado para ele. Para serem destinos válidos para arrastar, controles devem ser capazes de exibir o tipo de dados subjacentes do item arrastado para ele da **fontes de dados** janela. Por exemplo, não é válido arrastar um item que tenha um tipo de dados <xref:System.DateTime> em um <xref:System.Windows.Forms.CheckBox>, porque o <xref:System.Windows.Forms.CheckBox> não é capaz de exibir uma data.  
  
## Associando a dados em controles individuais  
 Quando você associa uma fonte de dados para obter detalhes, cada coluna no conjunto de dados é associada a um controle separado.  
  
 ![Bind data source to details](../data-tools/media/raddata-bind-data-source-to-details.png "raddata Bind data source to details")  
  
> [!IMPORTANT]
>  Observe que na ilustração anterior está sendo arrastado da propriedade pedidos da tabela Customers, não da tabela Orders. Associando à propriedade Orders, comandos de navegação no feita no DataGridView são refletidos imediatamente nos controles de detalhes. Se foi arrastado da tabela Pedidos, os controles ainda poderá estar associados ao conjunto de dados, mas não eles não seriam sincronizados com o DataGridView.  
  
 A ilustração a seguir mostra o padrão controles ligados a dados que são adicionados ao formulário depois que a propriedade de pedidos na tabela Customers é associada a "Detalhes" na janela fontes de dados.  
  
 ![Orders table bound to details](~/docs/data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders table bound to details")  
  
 Observe também que cada controle tem uma marca inteligente que permite que as personalizações que se aplicam a esse controle somente.  
  
## Consulte também  
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)