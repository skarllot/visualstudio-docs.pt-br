---
title: "Adicionar controles personalizados &#224; janela fontes de dados | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.howtoaddcustomcontrol"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Janela fontes de dados, adicionando controles"
  - "controles [Visual Studio], adicionando a janela fontes de dados"
  - "DefaultBindingPropertyAttribute classe usando"
  - "LookupBindingPropertiesAttribute classe usando"
  - "ComplexBindingPropertiesAttribute classe usando"
  - "Janela fontes de dados, selecionando controles"
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 42
caps.handback.revision: 40
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adicionar controles personalizados &#224; janela fontes de dados
Quando você arrasta um item do **fontes de dados** janela para uma superfície de design para criar um controle ligado a dados, você pode selecionar o tipo de controle que você criar. Cada item na janela possui uma lista suspensa que exibe os controles que você pode escolher. O conjunto de controles associados a cada item é determinado pelo tipo de dados do item. Se o controle que você deseja criar não aparecer na lista, você pode seguir as instruções neste tópico para adicionar o controle à lista.  
  
 Para obter mais informações sobre como selecionar controles ligados a dados para criar itens na **fontes de dados** janela, consulte [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
> [!NOTE]
>  Caixas de diálogo e comandos de menu que você vê podem diferir daqueles descritos na Ajuda, dependendo de suas configurações ativas ou edição. Para alterar as configurações, selecione **Import and Export Settings** sobre o **ferramentas** menu. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
##  <a name="customizinglist"></a> Personalizar a lista de controles associáveis para um tipo de dados  
 Execute as seguintes etapas para adicionar ou remover controles da lista de controles disponíveis para itens do **fontes de dados** janela que têm um tipo de dados específico.  
  
#### Para selecionar os controles a serem listados para um tipo de dados  
  
1.  Certifique\-se de que o WPF Designer ou o Windows Forms Designer é aberto.  
  
2.  No **fontes de dados** clique em um item que faz parte de uma fonte de dados é adicionada à janela e clique no menu suspenso para o item.  
  
3.  No menu suspenso, clique em **Personalizar**. Uma das seguintes caixas de diálogo é aberta:  
  
    -   Se o Windows Forms Designer é aberto, o **Data UI Customization** página do **opções** caixa de diálogo é aberta.  
  
    -   Se o WPF Designer é aberto, o **Personalizar associação de controle** caixa de diálogo é aberta.  
  
4.  Na caixa de diálogo, selecione um tipo de dados de **tipo de dados** lista suspensa.  
  
    -   Para personalizar a lista de controles para uma tabela ou objeto, selecione **\[lista\]**.  
  
    -   Para personalizar a lista de controles para uma coluna de uma tabela ou uma propriedade de um objeto, selecione o tipo de dados da coluna ou propriedade no armazenamento de dados subjacente.  
  
    -   Para personalizar a lista de controles para exibir os objetos de dados que têm formas definidas pelo usuário, selecione **\[Other\]**. Por exemplo, selecione **\[Other\]** se seu aplicativo tiver um controle personalizado que exibe dados de mais de uma propriedade de um objeto específico.  
  
5.  No **associados controles** caixa, selecione cada controle que você deseja estar disponíveis para o tipo de dados selecionado ou desmarque a seleção de todos os controles que você deseja remover da lista.  
  
    > [!NOTE]
    >  Se o controle que você deseja selecionar não aparecerá no **associados controles** caixa, você deve adicionar o controle à lista. Para obter mais informações, consulte [adicionando controles para a lista de controles associados para um tipo de dados](#addingcontrols).  
  
6.  Clique em **OK**.  
  
7.  No **fontes de dados** janela, clique em um item de dados tipo que você associou a apenas um ou mais controles e clique no menu suspenso para o item.  
  
     Os controles que você selecionou no **associados controles** caixa agora aparecem no menu suspenso para o item.  
  
##  <a name="addingcontrols"></a> Adicionando controles à lista de controles associados para um tipo de dados  
 Se você deseja associar um controle com um tipo de dados, mas o controle não aparecer no **associados controles** caixa, você deve adicionar o controle à lista. O controle deve ser localizado na solução atual ou em um assembly referenciado, estar disponível no **Toolbox**, e ter um atributo que especifica o comportamento de ligação de dados do controle.  
  
#### Para adicionar controles à lista de controles associados  
  
1.  Adicione o controle desejado para o **Toolbox** clicando com o **Toolbox** e selecionando **Escolher itens**.  
  
     O controle deve ter um dos seguintes atributos.  
  
    |Atributo|Descrição|  
    |--------------|---------------|  
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|Implemente esse atributo em controles simples que exibem uma única coluna \(ou propriedade\) de dados, como um <xref:System.Windows.Forms.TextBox>.|  
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|Implemente este atributo em controles que exibem listas \(ou tabelas\) de dados, como um <xref:System.Windows.Forms.DataGridView>.|  
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|Implemente este atributo em controles que exibem listas \(ou tabelas\) de dados, mas também precisa apresentar uma única coluna ou propriedade, como um <xref:System.Windows.Forms.ComboBox>.|  
  
2.  Abra o **Data UI Customization** página do **opções** caixa de diálogo \(Windows Forms\) ou abra o **Personalizar associação de controle** caixa de diálogo \(WPF\). Para obter mais informações, consulte [Personalizar a lista de controles associáveis para um tipo de dados](#customizinglist).  
  
3.  No **associados controles** caixa, o controle que você acabou de adicionar ao **Toolbox** agora deve aparecer.  
  
    > [!NOTE]
    >  Somente controles que estão localizados dentro da solução atual ou em um assembly referenciado \(e que implementem um dos atributos de associação de dados na tabela anterior\) podem ser adicionados à lista de controles associados. Para associar dados a um controle personalizado que não está disponível na **fontes de dados** janela, arraste o controle do **Toolbox** para a superfície de design e, em seguida, arraste o item para vincular a partir o **fontes de dados** janela para o controle.  
  
## Consulte também  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)