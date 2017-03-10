---
title: "Associar controles WPF a dados no Visual Studio | Microsoft Docs"
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
  - "dados [WPF], exibindo"
  - "WPF, ligação de dados no Visual Studio"
  - "associação de dados WPF [Visual Studio]"
  - "exibindo dados de WPF"
  - "WPF [WPF], dados"
  - "Designer de WPF, associação de dados"
  - "associação de dados, WPF"
ms.assetid: e05a1e0c-5082-479d-bbc9-d395b0bc6580
caps.latest.revision: 36
caps.handback.revision: 34
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associar controles WPF a dados no Visual Studio
Você pode exibir dados para usuários do seu aplicativo pela vinculação de dados para [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] controles. Para criar esses controles ligados a dados, você pode arrastar itens do **fontes de dados** janela para o [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)] em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Este tópico descreve algumas das tarefas, ferramentas e classes que você pode usar para criar a associação de dados mais comuns [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] aplicativos.  
  
 Para obter informações gerais sobre como criar controles ligados a dados em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md). Para obter mais informações sobre [!INCLUDE[TLA#tla_titlewinclient](../data-tools/includes/tlasharptla_titlewinclient_md.md)] associação de dados, consulte [Visão geral de associação de dados](../Topic/Data%20Binding%20Overview.md).  
  
## Tarefas envolvidas na associando controles WPF a dados  
 A tabela a seguir lista as tarefas que podem ser realizadas arrastando itens do **fontes de dados** janela para o [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)].  
  
|Tarefa|Mais informações|  
|------------|----------------------|  
|Crie novos controles ligados a dados.<br /><br /> Vincule controles existentes a dados.|[Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Associar controles WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md)|  
|Criar controles que exibem dados relacionados em uma relação pai\-filho: quando o usuário seleciona um registro de dados pai em um controle, o outro controle exibe dados filho relacionados para o registro selecionado.|[Exibir dados relacionados em aplicativos WPF](../data-tools/display-related-data-in-wpf-applications.md)|  
|Criar um *tabela de pesquisa* que exibe informações de uma tabela com base no valor de um campo de chave estrangeira em outra tabela.|[Criar tabelas de pesquisa em aplicativos do WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)|  
|Associar um controle a uma imagem em um banco de dados.|[Associar controles a imagens de um banco de dados](../data-tools/bind-controls-to-pictures-from-a-database.md)|  
  
## Destinos depósitos válidos  
 Você pode arrastar itens do **fontes de dados** janela apenas para destinos depósitos válidos no [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)]. Há dois tipos principais de destinos depósitos válidos: contêineres e controles. Um contêiner é um elemento de interface do usuário que normalmente contém controles. Por exemplo, uma grade é um contêiner, e então é uma janela.  
  
## XAML e código gerados  
 Quando você arrasta um item do **fontes de dados** janela para o [!INCLUDE[wpfdesigner_current_short](../data-tools/includes/wpfdesigner_current_short_md.md)], [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que define um novo controle ligado a dados \(ou associa um controle existente para a fonte de dados\). Para algumas fontes de dados, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também gera código no arquivo de code\-behind que preenche a fonte de dados com dados.  
  
 A seguinte tabela lista o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] e o código [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera para cada tipo de fonte de dados de **fontes de dados** janela.  
  
|Fonte de dados|Gerar XAML que associa um controle à fonte de dados|Gerar código que preenche a fonte de dados com dados|  
|--------------------|---------------------------------------------------------|----------------------------------------------------------|  
|Conjunto de dados|Sim|Sim|  
|[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]|Sim|Sim|  
|Serviço|Sim|Não|  
|Objeto|Sim|Não|  
  
### Conjuntos de dados  
 Quando você arrasta uma tabela ou coluna a partir de **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que faz o seguinte:  
  
-   Adiciona o conjunto de dados e um novo <xref:System.Windows.Data.CollectionViewSource> os recursos do contêiner arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados no conjunto de dados.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o XAML associará o controle ao item. Se você arrastar o item para um contêiner, o XAML cria o controle selecionado para o item arrastado e associará o controle ao item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] também faz as seguintes alterações no arquivo code\-behind:  
  
-   Cria um <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos para o [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] elemento que contém o controle. O manipulador de eventos preenche a tabela com dados, recupera o <xref:System.Windows.Data.CollectionViewSource> de contêiner recursos e, em seguida, faz o primeiro item dados o item atual. Se um <xref:System.Windows.FrameworkElement.Loaded> já existe um manipulador de eventos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adiciona este código ao manipulador de eventos existente.  
  
### Modelos de dados de entidade  
 Quando você arrasta uma entidade ou uma propriedade de entidade a partir de **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que faz o seguinte:  
  
-   Adiciona um novo <xref:System.Windows.Data.CollectionViewSource> os recursos do contêiner arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados na entidade.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associará o controle ao item. Se você arrastar o item para um contêiner, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] cria o controle que foi selecionado para o item arrastado e associará o controle ao item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
 Visual Studio também faz as seguintes alterações para o arquivo code\-behind:  
  
-   Adiciona um novo método que retorna uma consulta para a entidade que você arrastou para o designer \(ou a entidade que contém a propriedade que você arrastou para o designer\). O novo método tem o nome Get*EntityName*consulta, onde *EntityName* é o nome da entidade.  
  
-   Cria um <xref:System.Windows.FrameworkElement.Loaded> manipulador de eventos para o [!INCLUDE[TLA2#tla_ui](../data-tools/includes/tla2sharptla_ui_md.md)] elemento que contém o controle. O manipulador de eventos chama Get*EntityName*consultar o método para preencher a entidade com dados, recupera o <xref:System.Windows.Data.CollectionViewSource> de contêiner recursos e, em seguida, faz o primeiro item dados o item atual. Se um <xref:System.Windows.FrameworkElement.Loaded> já existe um manipulador de eventos, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] adiciona este código ao manipulador de eventos existente.  
  
### Serviços  
 Quando você arrasta um objeto de serviço ou a propriedade a partir de **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que cria um controle ligado a dados \(ou associa um controle existente para o objeto ou propriedade\). No entanto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não gera código que preenche o objeto de serviço de proxy com dados. Você deve escrever esse código. Para obter um exemplo que demonstra como fazer isso, consulte [Associar controles WPF a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
 O Visual Studio gera XAML que faz o seguinte:  
  
-   Adiciona um novo <xref:System.Windows.Data.CollectionViewSource> os recursos do contêiner que você arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados no objeto que é retornado pelo serviço.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] associará o controle ao item. Se você arrastar o item para um contêiner, o [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] cria o controle que foi selecionado para o item arrastado e associará o controle ao item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
### Objetos  
 Quando você arrasta um objeto ou propriedade do **fontes de dados** janela para o designer, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que cria um controle ligado a dados \(ou associa um controle existente para o objeto ou propriedade\). No entanto, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] não gera código para preencher o objeto com dados. Você deve escrever esse código.  
  
> [!NOTE]
>  Classes personalizadas devem ser público e ter um construtor sem parâmetros padrão. Eles não podem ser classes aninhadas com um ponto na sintaxe. Para obter mais informações, consulte [XAML e Classes personalizadas para WPF](../Topic/XAML%20and%20Custom%20Classes%20for%20WPF.md).  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gera [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] que faz o seguinte:  
  
-   Adiciona um novo <xref:System.Windows.Data.CollectionViewSource> os recursos do contêiner que você arrastados para o item. O <xref:System.Windows.Data.CollectionViewSource> é um objeto que pode ser usado para navegar e exibir os dados no objeto.  
  
-   Cria uma associação de dados para um controle. Se você arrastar o item para um controle existente no designer, o XAML associará o controle ao item. Se você arrastar o item para um contêiner, o XAML cria o controle selecionado para o item arrastado e associará o controle ao item. O controle é criado dentro de um novo <xref:System.Windows.Controls.Grid>.  
  
## Consulte também  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)