---
title: "Atualiza&#231;&#227;o hier&#225;rquica | Microsoft Docs"
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
  - "dados [Visual Basic], atualização hierárquica"
  - "conjuntos de dados [Visual Basic], atualização hierárquica"
  - "atualização hierárquica"
  - "salvamento de dados modificados"
  - "tabelas relacionadas, salvar"
  - "salvando dados, dados alterados"
  - "salvando dados, atualização hierárquica"
  - "salvando dados atualizados"
  - "salvamento de dados atualizados"
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
caps.latest.revision: 26
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Atualiza&#231;&#227;o hier&#225;rquica
*Atualização hierárquica* refere\-se ao processo de salvar dados atualizados \(de um dataset com duas ou mais tabelas relacionadas\) para um banco de dados mantendo regras de integridade referencial.*a integridade referencial* refere\-se às regras de consistência fornecido pelas restrições em um banco de dados que controlam o comportamento de inserir, atualizar e excluir registros relacionados. Por exemplo, é a integridade referencial que aplica a criação de um registro de cliente antes de permitir pedidos a ser criado para esse cliente.  Para obter mais informações sobre relacionamentos em conjuntos de dados, consulte [Relacionamentos em conjuntos de dados](../data-tools/relationships-in-datasets.md)  
  
 O recurso de atualização hierárquica usa um `TableAdapterManager` para gerenciar o `TableAdapter`s em um dataset tipado. O `TableAdapterManager` componente é um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]— gerado de classe, portanto, não é parte do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Quando você arrasta uma tabela da janela fontes de dados a uma página de formulário do Windows Forms ou WPF, o Visual Studio adiciona uma variável do tipo TableAdapterManager à classe de formulário ou página e vê\-lo no designer na bandeja de componentes. Para obter informações detalhadas sobre o `TableAdapterManager` de classe, consulte a seção TableAdapterManager Reference do [Visão geral de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Por padrão, um conjunto de dados trata tabelas relacionadas como "apenas relações" o que significa que ele não impõe restrições de chave estrangeira. Você pode modificar essa configuração em tempo de design usando o designer de conjunto de dados. Clique na linha de relação entre duas tabelas para abrir a caixa de diálogo relação. As alterações feitas aqui determinam como o TableAdapterManager se comporta quando ele envia as alterações nas tabelas relacionadas no banco de dados.  
  
## Habilitando atualização hierárquica em um conjunto de dados  
 Por padrão, a atualização hierárquica está habilitada para todos os novos conjuntos de dados que são adicionados ou criados em um projeto. Ativar ou desativar o atualização hierárquica definindo a **Hierarchical Update** propriedade de um dataset tipado no [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md) para **True** ou **False**:  
  
 ![Hierarchical update setting](../data-tools/media/hierarchical-update-setting.png "Hierarchical update setting")  
  
## Criar uma nova relação entre tabelas  
 Para criar uma nova relação entre duas tabelas no Dataset Designer, selecione a barra de título de cada tabela, em seguida, clique com botão direito e escolha **Adicionar relação**.  
  
 ![Hierarchical update add relation menu](~/docs/data-tools/media/hierarchical-update-add-relation-menu.png "Hierarchical update add relation menu")  
  
## Restrições de chave estrangeira e atualizações em cascata e exclusões  
 É importante compreender como restrições de chave externa e comportamento em cascata no banco de dados são criados no código de dataset gerado.  
  
 Por padrão, as tabelas de dados em um conjunto de dados são geradas com relacionamentos \(<xref:System.Data.DataRelation>\) que coincidem com os relacionamentos no banco de dados. No entanto, o relacionamento no dataset não é gerado como uma restrição de chave estrangeira. O <xref:System.Data.DataRelation> é configurado como **relação somente** sem um <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> ou <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> em vigor.  
  
 Por padrão, atualizações em cascata e exclusões em cascata estão desativadas mesmo se a relação do banco de dados é definida com atualizações em cascata e\/ou exclusões em cascata ativadas. Por exemplo, criar um novo cliente e um novo pedido e, em seguida, tentar salvar os dados podem causar um conflito com as restrições de chave estrangeira definidas no banco de dados. Para obter mais informações, consulte [Como configurar restrições de chave estrangeira em um conjunto de dados](../Topic/How%20to:%20Configure%20Foreign-Key%20Constraints%20in%20a%20Dataset.md).  
  
## Definindo a ordem para executar atualizações  
 Definindo a ordem para executar atualizações define a ordem da pessoa inserções, atualizações e exclusões necessárias para salvar todos os dados modificados em todas as tabelas de um dataset. Quando a atualização hierárquica está habilitada, inserções são executadas em primeiro lugar, em seguida, atualiza e exclui. O `TableAdapterManager` fornece um `UpdateOrder` propriedade que pode ser definida para executar atualizações em primeiro lugar, em seguida, inserções e exclusões.  
  
> [!NOTE]
>  É importante entender que a ordem de atualização é exaustiva. Isto é, quando as atualizações são executadas, inserções são executadas para todas as tabelas no dataset, em seguida, atualizações são realizadas para todas as tabelas no dataset e, em seguida, exclusões são realizadas para todas as tabelas no dataset.  
  
 Para definir o `UpdateOrder` propriedade após arrastar itens do [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md) para um formulário, clique no `TableAdapterManager` na bandeja de componentes e definir o `UpdateOrder` propriedade o **propriedades** janela. Para obter mais informações, consulte [Como definir a ordem ao executar uma atualização hierárquica](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md).  
  
## Criando uma cópia de Backup de um conjunto de dados antes de executar uma atualização hierárquica  
 Quando você salva dados \(chamando o `TableAdapterManager.UpdateAll()` método\), o `TableAdapterManager` tenta atualizar os dados para cada tabela em uma única transação. Se qualquer parte da atualização para qualquer tabela falhar, a transação inteira é revertida. Na maioria das situações, a reversão da transação retorna seu aplicativo para seu estado original. No entanto, talvez você deseje restaurar o conjunto de dados da cópia de backup. Um exemplo é quando você está usando valores de incremento automático. Por exemplo, se salvar operação não for bem\-sucedida, os valores de incremento automático não são redefinidos no conjunto de dados e o dataset continuará a criar valores de incremento automático, deixando um intervalo na numeração que pode não ser aceitável em seu aplicativo. Em situações em que isso é um problema, o `TableAdapterManager` fornece um `BackupDataSetBeforeUpdate` propriedade que substitui o conjunto de dados existente por uma cópia de backup se a transação falhar.  
  
> [!NOTE]
>  A cópia de backup está apenas na memória durante a execução de `TableAdapterManager.UpdateAll` método. Portanto, não há nenhum acesso programático a esse conjunto de dados de backup porque ele substitui o conjunto de dados original ou sai do escopo assim que o `TableAdapterManager.UpdateAll` método concluiu a execução.  
  
## Modificando o código salvar gerado para executar a atualização hierárquica  
 Salve as alterações das tabelas relacionadas de dados no conjunto de dados no banco de dados chamando o `TableAdapterManager.UpdateAll` método e passando o nome do conjunto de dados que contém as tabelas relacionadas. Por exemplo, execute o `TableAdapterManager.UpdateAll(NorthwindDataset)` método para enviar atualizações de todas as tabelas no NorthwindDataset para o banco de dados de back\-end.  
  
 Depois de soltar os itens do **fontes de dados** janela, código é adicionado automaticamente para o `Form_Load` evento para preencher cada tabela \(o `TableAdapter.Fill` métodos\). Código também é adicionado ao **Salvar** evento de clique de botão a <xref:System.Windows.Forms.BindingNavigator> para salvar dados do conjunto de dados no banco de dados \(o `TableAdapterManager.UpdateAll` método\).  
  
 O código salvar gerado também contém uma linha de código que chama o `CustomersBindingSource.EndEdit` método. Mais especificamente, ele chama o <xref:System.Windows.Forms.BindingSource.EndEdit%2A> método do primeiro <xref:System.Windows.Forms.BindingSource> adicionado ao formulário. Em outras palavras, esse código é gerado apenas para a primeira tabela arrastada do **fontes de dados** window para o formulário. O <xref:System.Windows.Forms.BindingSource.EndEdit%2A> chamada confirma as alterações que estão em processo em quaisquer controles ligados a dados que estão sendo editados atualmente. Portanto, se um controle ligado a dados ainda tem foco e você clicar o **Salvar** botão, todas as edições pendentes nesse controle serão confirmadas antes de salvar \(o `TableAdapterManager.UpdateAll` método\).  
  
> [!NOTE]
>  O designer adiciona o `BindingSource.EndEdit` código para a primeira tabela arrastada para o formulário. Portanto, você precisa adicionar uma linha de código para chamar o `BindingSource.EndEdit` método para cada tabela relacionada no formulário. Para este passo a passo, isso significa que você precisa adicionar uma chamada para o `OrdersBindingSource.EndEdit` método.  
  
#### Para atualizar o código para confirmar as alterações nas tabelas relacionadas antes de salvar  
  
1.  Clique duas vezes o **Salvar** botão o <xref:System.Windows.Forms.BindingNavigator> Abrir **Form1** no Editor de códigos.  
  
2.  Adicionar uma linha de código para chamar o `OrdersBindingSource.EndEdit` método após a linha que chama o `CustomersBindingSource.EndEdit` método. O código de **Salvar** clique no botão eventos devem se parecer com o seguinte:  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-cs[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]  
  
 Além de confirmar as alterações em uma tabela filho relacionada antes de salvar dados em um banco de dados, você também terá que registros pai de confirmação recém\-criados antes de adicionar novos registros filho a um conjunto de dados. Em outras palavras, você talvez precise adicionar o novo registro pai \(cliente\) para o conjunto de dados antes das restrições de chave estrangeiras habilitar novos registros filho \(pedidos\) sejam adicionados ao conjunto de dados. Para fazer isso, você pode usar o filho `BindingSource.AddingNew` eventos.  
  
> [!NOTE]
>  Você pode ou não ter de confirmar novos registros pai; ele depende do tipo de controle que é usado para vincular a sua fonte de dados. Neste passo a passo, você usa controles individuais para associar à tabela pai; Isso requer o código adicional para confirmar o novo registro pai. Se os registros pai foram exibidos em um controle complexo de associação como o <xref:System.Windows.Forms.DataGridView>, adicionais neste <xref:System.Windows.Forms.BindingSource.EndEdit%2A> chamada para o registro pai não seria necessário. Isso ocorre porque a funcionalidade de associação de dados subjacente do controle manipula a confirmação dos novos registros.  
  
#### Para adicionar código para confirmar registros pai no conjunto de dados antes de adicionar novos registros filho  
  
1.  Criar um manipulador de eventos para o `OrdersBindingSource.AddingNew` evento.  
  
    -   Abra **Form1** no modo design, clique em **OrdersBindingSource** na bandeja de componentes, selecione **eventos** no **propriedades** janela e clique duas vezes o **AddingNew** eventos.  
  
2.  Adicione ao manipulador de eventos uma linha de código que chama o `CustomersBindingSource.EndEdit` método. O código de `OrdersBindingSource_AddingNew` manipulador de eventos deve se parecer com o seguinte:  
  
     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-cs[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]  
  
## Referência de TableAdapterManager  
 Por padrão, um `TableAdapterManager` classe é gerada quando você cria um conjunto de dados que contém tabelas relacionadas. Para impedir que a classe que está sendo gerado, altere o valor de `Hierarchical Update` propriedade do conjunto de dados como false. Quando você arrasta uma tabela que tenha uma relação na superfície de design de um Windows Form ou página WPF, o Visual Studio declara uma variável de membro da classe. Se você não usar a ligação de dados, você precisa declarar manualmente a variável.  
  
 O `TableAdapterManager` classe não é parte do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Portanto, você não pode procurar por ele na documentação. Ele é criado em tempo de design como parte do processo de criação de conjunto de dados.  
  
 A seguir estão os métodos usados frequentemente e propriedades do `TableAdapterManager` classe:  
  
|Membro|Descrição|  
|------------|---------------|  
|Método `UpdateAll`|Salva todos os dados de todas as tabelas de dados.|  
|`BackUpDataSetBeforeUpdate` propriedade|Booleano. Determina se deve criar uma cópia de backup do conjunto de dados antes de executar o `TableAdapterManager.UpdateAll` método.|  
|*tableName* `TableAdapter` propriedade|Representa um `TableAdapter`. Gerado `TableAdapterManager` contém uma propriedade para cada `TableAdapter` que ele gerencia. Por exemplo, um conjunto de dados com uma tabela clientes e pedidos é gerado com um `TableAdapterManager` que contém `CustomersTableAdapter` e `OrdersTableAdapter` Propriedades.|  
|`UpdateOrder` propriedade|Controla a ordem de execução dos comandos individuais Insert, Update e Delete. Defina\-o para um dos valores a `TableAdapterManager.UpdateOrderOption` enumeração.<br /><br /> Por padrão, o `UpdateOrder` é definido como **InsertUpdateDelete**. Isso significa que inserções são executadas para todas as tabelas no dataset, em seguida, atualizações são realizadas para todas as tabelas no dataset e, em seguida, exclui são executadas para todas as tabelas no dataset. Para obter mais informações, consulte [Como definir a ordem ao executar uma atualização hierárquica](../Topic/How%20to:%20Set%20the%20Order%20When%20Performing%20a%20Hierarchical%20Update.md).|  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)