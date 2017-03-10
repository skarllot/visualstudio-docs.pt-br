---
title: "Associar objetos no Visual Studio | Microsoft Docs"
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
  - "associação de objeto de dados [Visual Studio]"
  - "dados [Visual Studio], associando a objetos"
  - "associação de objeto"
  - "associando a objetos"
ms.assetid: ed743ce6-73af-45e5-a8ff-045eddaccc86
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Associar objetos no Visual Studio
Visual Studio fornece ferramentas em tempo de design para trabalhar com objetos personalizados \(ao contrário de outras fontes de dados como entidades, conjuntos de dados e serviços\) como a fonte de dados em seu aplicativo. Quando você deseja armazenar os dados de um banco de dados em um objeto que você associar a controles de interface do usuário, a abordagem recomendada é usar o Entity Framework para gerar a classe ou classes. EF irá gerar automaticamente todo o código de controle de alterações de texto clichê, o que significa que quaisquer alterações feitas nos objetos locais automaticamente serão persistentes no banco de dados quando você chamar AcceptChanges no objeto DbSet.    Para obter mais informações, consulte [documentação do Entity Framework](https://ef.readthedocs.org/en/latest/).  
  
> [!TIP]
>  As abordagens para associação de objeto neste artigo só devem ser consideradas se seu aplicativo já com base em conjuntos de dados ou se você já estiver familiarizado com conjuntos de dados e os dados que forem processados tabular e não muito complexa ou muito grande. Para obter um exemplo ainda mais simples de carregamento de dados diretamente em objetos usando um DataReader e atualizar manualmente a interface do usuário sem ligação de dados, consulte [Criar um aplicativo simples de dados usando o ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
## Requisitos de objeto  
 O único requisito de objetos personalizados trabalhar com os dados, ferramentas de design no Visual Studio é que o objeto precisa de pelo menos uma propriedade pública.  
  
 Em geral, objetos personalizados não exigem qualquer interfaces específicas, construtor ou atributos para agir como uma fonte de dados para um aplicativo. No entanto, se você deseja arrastar o objeto a partir o **fontes de dados** janela para uma superfície de design para criar um controle ligado a dados, e se o objeto implementa a <xref:System.ComponentModel.ITypedList> ou <xref:System.ComponentModel.IListSource> interface, o objeto deve ter um construtor padrão. Caso contrário, o Visual Studio não é possível instanciar o objeto de fonte de dados, e ele exibirá um erro quando você arrasta o item para a superfície de design.  
  
## Exemplos de como usar objetos personalizados como fontes de dados  
 Enquanto houver incontáveis maneiras de implementar a lógica do aplicativo ao trabalhar com objetos como uma fonte de dados, para o SQL há bancos de dados são poucas operações padrões que podem ser simplificadas usando os objetos TableAdapter gerados do Visual Studio. Esta página explica como implementar esses processos padrões usando TableAdapters; ele não se destina como um guia para a criação de seus objetos personalizados. Por exemplo, normalmente você executará as seguintes operações padrões independentemente da implementação específica de seus objetos, ou lógica do aplicativo:  
  
-   Carregando dados em objetos \(normalmente de um banco de dados\).  
  
-   Criando uma coleção tipada de objetos.  
  
-   Adicionando objetos e remover objetos de uma coleção.  
  
-   Exibir os dados de objeto aos usuários em um formulário.  
  
-   Alteração\/edição de dados em um objeto.  
  
-   Salvar dados de objetos no banco de dados.  
  
> [!NOTE]
>  Para melhor entender e fornecer contexto para os exemplos nesta página, é recomendável que você conclua o seguinte: [Instruções passo a passo: conectando a dados em objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md). Essa explicação passo a passo cria os objetos discutidos nesta página de Ajuda.  
  
### Carregando dados em objetos  
 Para este exemplo, você pode carregar dados para os objetos usando TableAdapters. Por padrão, os TableAdapters são criados com dois tipos de métodos que buscam dados de um banco de dados e popular tabelas de dados.  
  
-   O `TableAdapter.Fill` método preenche uma tabela de dados existente com os dados retornados.  
  
-   O `TableAdapter.GetData` método retorna uma nova tabela de dados preenchida com dados.  
  
 A maneira mais fácil de carregar os objetos personalizados com dados é chamar o `TableAdapter.GetData` método, percorrer a coleção de linhas na tabela de dados retornados e preencher cada objeto com os valores em cada linha. Você pode criar um `GetData` método que retorna uma tabela de dados preenchida para qualquer consulta adicionada a um TableAdapter.  
  
> [!NOTE]
>  Visual Studio nomeia as consultas TableAdapter `Fill` e `GetData` por padrão, mas esses nomes podem ser alterados para qualquer nome de método válido.  
  
 O exemplo a seguir mostra como percorrer as linhas em uma tabela de dados e preencher um objeto com dados:  
  
 [!code-cs[VbRaddataConnecting#4](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_1.cs)]
 [!code-vb[VbRaddataConnecting#4](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_1.vb)]  
  
### Criando uma coleção tipada de objetos  
 Você pode criar classes de coleção para os objetos ou usar as coleções tipadas que são automaticamente fornecidas pelo [Componente BindingSource](../Topic/BindingSource%20Component.md).  
  
 Quando você estiver criando uma classe de coleção personalizada para objetos, é recomendável que você herde da <xref:System.ComponentModel.BindingList%601>. Essa classe genérica fornece funcionalidade para administrar sua coleção, bem como a capacidade de gerar eventos que enviam notificações para a infra\-estrutura de ligação de dados no Windows Forms.  
  
 A coleção gerada automaticamente na <xref:System.Windows.Forms.BindingSource> usa um <xref:System.ComponentModel.BindingList%601> para sua coleção tipada. Se seu aplicativo não requer funcionalidade adicional, você pode manter sua coleção dentro do <xref:System.Windows.Forms.BindingSource>. Para obter mais informações, consulte o <xref:System.Windows.Forms.BindingSource.List%2A> propriedade o <xref:System.Windows.Forms.BindingSource> classe.  
  
> [!NOTE]
>  Se sua coleção exigir funcionalidade não fornecida pela implementação base da <xref:System.ComponentModel.BindingList%601>, então você deve criar uma coleção personalizada para que você possa adicionar à classe conforme necessário.  
  
 O código a seguir mostra como criar a classe para uma coleção fortemente tipada de `Order` objetos:  
  
 [!code-cs[VbRaddataConnecting#8](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_2.cs)]
 [!code-vb[VbRaddataConnecting#8](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_2.vb)]  
  
### Adicionando objetos a uma coleção  
 Adicionar objetos a uma coleção, chamando o `Add` método de sua classe de coleção personalizada ou do <xref:System.Windows.Forms.BindingSource>.  
  
 Para obter um exemplo de como adicionar a uma coleção usando um <xref:System.Windows.Forms.BindingSource>, consulte o `LoadCustomers` método [Instruções passo a passo: conectando a dados em objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
 Para obter um exemplo de como adicionar objetos a uma coleção personalizada, consulte o `LoadOrders` método [Instruções passo a passo: conectando a dados em objetos \(Windows Forms\)](../Topic/Walkthrough:%20Connecting%20to%20Data%20in%20Objects%20\(Windows%20Forms\).md).  
  
> [!NOTE]
>  O `Add` método é fornecido automaticamente para sua coleção personalizada quando você herda do <xref:System.ComponentModel.BindingList%601>.  
  
 O código a seguir mostra como adicionar objetos a uma coleção tipada em um <xref:System.Windows.Forms.BindingSource>:  
  
 [!code-cs[VbRaddataConnecting#5](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_3.cs)]
 [!code-vb[VbRaddataConnecting#5](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_3.vb)]  
  
 O código a seguir mostra como adicionar objetos a uma coleção tipada que herda do <xref:System.ComponentModel.BindingList%601>:  
  
> [!NOTE]
>  Neste exemplo o `Orders` coleção é uma propriedade do `Customer` objeto.  
  
 [!code-cs[VbRaddataConnecting#6](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_4.cs)]
 [!code-vb[VbRaddataConnecting#6](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_4.vb)]  
  
### Remover objetos de uma coleção  
 Remover objetos de uma coleção, chamando o `Remove` ou `RemoveAt` método de sua classe de coleção personalizada ou do <xref:System.Windows.Forms.BindingSource>.  
  
> [!NOTE]
>  O `Remove` e `RemoveAt` métodos são fornecidos automaticamente para sua coleção personalizada quando você herda do <xref:System.ComponentModel.BindingList%601>.  
  
 O código a seguir mostra como localizar e remover objetos da coleção tipada em um <xref:System.Windows.Forms.BindingSource> com o <xref:System.Windows.Forms.BindingSource.RemoveAt%2A> método:  
  
 [!code-cs[VbRaddataConnecting#7](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_5.cs)]
 [!code-vb[VbRaddataConnecting#7](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_5.vb)]  
  
### Exibindo dados de objeto para usuários  
 Para exibir os dados em objetos para usuários, você cria uma fonte de dados de objeto usando o **Data Source Configuration Wizard**, e, em seguida, arraste o objeto inteiro ou propriedades individuais para seu formulário a partir de **fontes de dados** janela.  
  
### Modificando os dados em objetos  
 Para editar dados em objetos personalizados que são associados a dados a controles de Windows Forms, basta edite os dados no controle de limite \(ou diretamente nas propriedades do objeto\). Arquitetura de ligação de dados irá atualizar os dados no objeto.  
  
 Se seu aplicativo exigir o rastreamento de alterações e recuo nas alterações propostas para seus valores originais, você deve implementar essa funcionalidade no seu modelo de objeto. Para obter exemplos de como tabelas de dados manter controle de alterações propostas, consulte <xref:System.Data.DataRowState>, <xref:System.Data.DataSet.HasChanges%2A>, e <xref:System.Data.DataTable.GetChanges%2A>.  
  
### Salvando dados em objetos do banco de dados  
 Você pode salvar dados no banco de dados, passando os valores de seu objeto para métodos DBDirect do TableAdapter.  
  
 O Visual Studio cria métodos DBDirect que podem ser executados diretamente no banco de dados. Esses métodos não requerem objetos DataSet ou DataTable.  
  
|Método TableAdapter DBDirect|Descrição|  
|----------------------------------|---------------|  
|`TableAdapter.Insert`|Adiciona novos registros em um banco de dados, permitindo que você passe valores individuais de coluna como parâmetros do método.|  
|`TableAdapter.Update`|Atualizações de registros existentes em um banco de dados. O método Update aceita valores da coluna original e novo como parâmetros de método. Os valores originais são usados para localizar o registro original e os novos valores são usados para atualizar esse registro.<br /><br /> O `TableAdapter.Update` método também é usado para acomodar as alterações em um conjunto de dados no banco de dados fazendo uma <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, <xref:System.Data.DataRow>, ou uma matriz de <xref:System.Data.DataRow>s como parâmetros do método.|  
|`TableAdapter.Delete`|Exclui registros existentes do banco de dados com base em valores da coluna original passados como parâmetros de método.|  
  
 Para salvar dados de uma coleção de objetos, percorrer a coleção de objetos \(por exemplo, usando um loop for\-next\) e envie os valores para cada objeto de banco de dados usando métodos DBDirect do TableAdapter.  
  
 O exemplo a seguir mostra como usar o `TableAdapter.Insert` Método DBDirect para adicionar um novo cliente diretamente ao banco de dados:  
  
 [!code-cs[VbRaddataSaving#23](../data-tools/codesnippet/CSharp/bind-objects-in-visual-studio_6.cs)]
 [!code-vb[VbRaddataSaving#23](../data-tools/codesnippet/VisualBasic/bind-objects-in-visual-studio_6.vb)]  
  
## Consulte também  
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)