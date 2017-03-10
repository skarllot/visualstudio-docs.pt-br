---
title: "Caixa de di&#225;logo Personalizar Associa&#231;&#227;o de Controle | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datauicustomization"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "caixa de diálogo Personalizar Associação de Controle"
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Caixa de di&#225;logo Personalizar Associa&#231;&#227;o de Controle
Use o  **Personalizar a vinculação de controle** caixa de diálogo para especificar quais controles estão disponíveis para itens na [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md).  
  
 Cada item da  **Fontes de dados** janela possui uma lista de associados de controles que podem ser vinculados ao item.  Os controles disponíveis para cada item são determinados pelo tipo de dados do item.  Cada tipo de dados possui uma lista de controles associados válidos definidos nesta caixa de diálogo, incluindo um controle padrão.  
  
 Antes de arrastar um item para uma superfície de design para criar um controle ligado a dados, você pode selecionar qual controle para criar.  Se você arrastar um item da  **Fontes de dados** janela na superfície de design, sem selecionar um controle, o controle padrão para o tipo de dados do item selecionado é adicionado à superfície de design.  
  
 Para obter mais informações sobre como usar essa caixa de diálogo para personalizar a lista de controles para itens na  **Fontes de dados** janela, consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## Lista UIElement  
 **Tipo de dados**  
 Exibe uma lista de tipos que você associa aos controles:  
  
-   Tabelas, entidades e objetos são representados como  **\[lista\]** tipos.  
  
-   Colunas ou propriedades públicas de entidades e os objetos são representadas como o tipo de dados da coluna ou propriedade no armazenamento de dados subjacente.  
  
-   Objetos com formas definidas pelo usuário são representados como **\[Other\]**.  Por exemplo, se seu aplicativo tiver um controle personalizado que exibe dados de mais de uma propriedade de um objeto, selecione o  **\[Other\]** o tipo de dados para o seu controle.  
  
 **Controles associados**  
 Exibe uma lista de controles que você pode associar um tipo de dados específico.  Se você deseja associar a um determinado controle com o tipo de dados selecionado no  **Tipo de dados** , selecione a caixa de seleção correspondente.  Desmarque o caixa de seleção para remover uma associação.  Verificados os controles aparecem no menu de atalho apresentado pelo  **Fontes de dados** janela para um item do tipo de dados associado.  
  
 Você pode adicionar controles à lista, adicionando controles que têm um dos vários atributos de vinculação de dados para o  **caixa de ferramentas**.  Para obter mais informações, consulte [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
 **Definir Padrão**  
 Atribui o tipo de controle selecionado para ser o padrão para itens do tipo de dados selecionado.  O controle padrão aparece como a primeira seleção no menu de atalho apresentada pelo  **Fontes de dados** janela para um item.  Tipo de apenas um controle pode ser atribuído como o padrão para um tipo de dados.  
  
 **Limpar Padrão**  
 Remove a designação de um controle como o padrão para o tipo de dados selecionado.  Se existe um padrão para o tipo de dados selecionados,  **\[Nenhum\]** aparece como a primeira seleção no menu de atalho apresentada pelo  **Fontes de dados** janela para um item do tipo associado.  
  
## Consulte também  
 [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md)   
 [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)   
 [Associar controles dos Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Adicionar controles personalizados à janela fontes de dados](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Como definir o controle a ser criado quando arrastado da janela Fontes de Dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)