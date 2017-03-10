---
title: "Passo a passo: Personalizando a inser&#231;&#227;o, atualiza&#231;&#227;o e exclus&#227;o de comportamento de classes de entidade | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03ff1146-706e-4780-91cb-56a83df63eea
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Passo a passo: Personalizando a inser&#231;&#227;o, atualiza&#231;&#227;o e exclus&#227;o de comportamento de classes de entidade
O [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornece uma superfície de design visual para criar e editar as classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] \(classes de entidade\) que são baseadas em objetos em um banco de dados.  Usando [LINQ to SQL](../Topic/LINQ%20to%20SQL.md), você pode usar a tecnologia LINQ para acessar os bancos de dados SQL.  Para obter mais informações, consulte [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md).  
  
 Por padrão, a lógica para executar atualizações é fornecida pelo tempo de execução do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  O tempo de execução cria instruções padrão Insert, Update e Delete com base no esquema da tabela \(as definições de coluna e as informações da chave primária\).  Quando você não deseja usar o comportamento padrão, poderá configurar o comportamento de atualização e designar procedimentos armazenados específicos para executar as inserções, as atualizações e as exclusões necessárias para trabalhar com os dados no banco de dados.  Você também pode fazer isso quando o comportamento padrão não é gerado, por exemplo, quando as classes de entidade mapeiam para as exibições.  Além disso, você pode substituir o comportamento de atualização padrão quando o banco de dados exige acesso à tabela por meio dos procedimentos armazenados.  Para obter mais informações, consulte [Customizing Operations By Using Stored Procedures](../Topic/Customizing%20Operations%20By%20Using%20Stored%20Procedures.md).  
  
> [!NOTE]
>  Essa explicação passo a passo exige a disponibilidade dos procedimentos armazenados **InsertCustomer**, **UpdateCustomer** e **DeleteCustomer** para o banco de dados Northwind.  Para obter detalhes sobre como criar esses procedimentos armazenados, consulte [Instruções passo a passo: criando procedimentos armazenados atualizados para a tabela Clientes do Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
 Essa explicação passo a passo fornece as etapas que você deve seguir para substituir o comportamento padrão de tempo de execução LINQ to SQL para salvar dados de volta para um banco de dados usando procedimentos armazenados.  
  
 Durante essa explicação passo a passo, será ensinado como realizar as seguintes tarefas:  
  
-   Crie um novo aplicativo do Windows Forms e adicione um arquivo [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a ele.  
  
-   Crie uma classe de entidade que está mapeada para a tabela Customers Northwind.  
  
-   Crie uma fonte de dados de objeto que referencia a classe de cliente LINQ to SQL.  
  
-   Crie um Windows Form que contém um <xref:System.Windows.Forms.DataGridView> que está associado à classe Customer.  
  
-   Implemente a funcionalidade de salvar para o formulário.  
  
-   Crie métodos de <xref:System.Data.Linq.DataContext> adicionando procedimentos armazenados ao [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
-   Configure a classe Customer para usar procedimentos armazenados para executar inserções, atualizações e exclusões.  
  
## Pré-requisitos  
 Para concluir esta explicação passo a passo, você precisará do seguinte:  
  
-   Acessar a versão do SQL Server do banco de dados de exemplo Northwind.  Para obter mais informações, consulte [Como instalar bancos de dados de exemplo](../data-tools/how-to-install-sample-databases.md).  
  
-   Os procedimentos armazenados **InsertCustomer**, **UpdateCustomer** e **DeleteCustomer** para o banco de dados Northwind.  Para obter mais informações, consulte [Instruções passo a passo: criando procedimentos armazenados atualizados para a tabela Clientes do Northwind](../data-tools/walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table.md).  
  
## Criando um aplicativo e adicionando classes LINQ to SQL  
 Como você estará trabalhando com classes do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] e exibindo os dados em um Windows Form, crie um novo aplicativo do Windows Forms e adicione um arquivo de classes LINQ to SQL.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Para criar um novo projeto de aplicativo do Windows que contém classes LINQ to SQL  
  
1.  No menu **Arquivo**, crie um novo projeto.  
  
2.  Dê ao projeto o nome UpdatingwithSProcsWalkthrough.  
  
    > [!NOTE]
    >  O [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] tem suporte em projetos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e C\#.  Portanto, crie o novo projeto em uma dessas linguagens.  
  
3.  Clique no modelo do **Aplicativo do Windows Forms** e clique em **OK**.  Para obter mais informações, consulte [Aplicativos cliente](../Topic/Developing%20Client%20Applications%20with%20the%20.NET%20Framework.md).  
  
     O projeto de UpdatingwithSProcsWalkthrough é criado e adicionado ao **Gerenciador de Soluções**.  
  
4.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
5.  Clique no modelo **Classes LINQ to SQL** e digite Northwind.dbml na caixa **Nome**.  
  
6.  Clique em **Adicionar**.  
  
     Um arquivo de classes LINQ to SQL vazio \(Northwind.dbml\) é adicionado ao projeto, e o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] é aberto.  
  
## Criando a Classe Entidade de Cliente e o Objeto de Fonte de Dados  
 Crie classes [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] que são mapeadas para tabelas de banco de dados arrastando tabelas do **Gerenciador de Servidores**\/**Database Explorer** para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  O resultado são classes de entidade do LINQ to SQL que mapeiam para as tabelas no banco de dados.  Depois de criar classes de entidade, elas podem ser usadas como fontes de dados de objeto assim como outras classes que têm propriedades públicas.  
  
#### Para criar uma classe de entidade Customer e configurar uma fonte de dados com ela  
  
1.  No **Gerenciador de Servidores**\/**Database Explorer**, localize a tabela Customer na versão do SQL Server do banco de dados de exemplo Northwind.  Para obter mais informações, consulte [Como se conectar ao banco de dados Northwind](../data-tools/how-to-connect-to-the-northwind-database.md).  
  
2.  Arraste o nó **Customers** do **Gerenciador de Servidores**\/**Database Explorer** para a superfície do [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Uma classe de entidade chamada **Customer** é criada.  Ela tem propriedades que correspondem às colunas na tabela Customers.  A classe de entidade é chamada de **Customer** \(não **Customers**\) porque representa um único cliente da tabela Customers.  
  
    > [!NOTE]
    >  Esse comportamento de renomeação é chamado de *pluralização*.  Ele pode ser ativado ou desativado na [Caixa de diálogo Opções](../ide/reference/options-dialog-box-visual-studio.md).  Para obter mais informações, consulte [Como: ative em pluralization e off \(Object Relational Designer\)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md).  
  
3.  No menu **Compilar**, clique em **Compilar UpdatingwithSProcsWalkthrough** para criar o projeto.  
  
4.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
5.  Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
6.  Clique em **Objeto** na página **Escolher um Tipo de Fonte de Dados** e clique em **Avançar**.  
  
7.  Expanda o nó **UpdatingwithSProcsWalkthrough** e localize e selecione a classe **Customer**.  
  
    > [!NOTE]
    >  Se a classe **Customer** não estiver disponível, cancele o assistente, compile o projeto e execute o assistente novamente.  
  
8.  Clique em **Concluir** para criar a fonte de dados e adicionar a classe de entidade **Customer** à janela **Fontes de Dados**.  
  
## Criando um DataGridView para exibir os dados do cliente em um Windows Form  
 Crie controles que estão associados a classes de entidade arrastando os itens de fonte de dados do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] da janela **Fontes de Dados** para um Windows Form.  
  
#### Para adicionar controles que estão associados às classes de entidade  
  
1.  Abrir Form1 na exibição Design.  
  
2.  Da janela **Fontes de Dados**, arraste o nó **Customer** para o Form1.  
  
    > [!NOTE]
    >  Para exibir a janela **Fontes de Dados**, clique em **Mostrar Fontes de Dados** no menu **Dados**.  
  
3.  Abra o Form1 no Editor de Códigos.  
  
4.  Adicione o seguinte código ao formulário, global para o formulário, fora de qualquer método específico, mas dentro da classe Form1:  
  
    ```vb#  
    Private NorthwindDataContext1 As New NorthwindDataContext  
    ```  
  
    ```c#  
    private NorthwindDataContext northwindDataContext1  
        = new NorthwindDataContext();  
  
    ```  
  
5.  Crie um manipulador de eventos para o evento `Form_Load` e adicione o seguinte código ao manipulador:  
  
    ```vb#  
    CustomerBindingSource.DataSource = NorthwindDataContext1.Customers  
    ```  
  
    ```c#  
    customerBindingSource.DataSource  
        = northwindDataContext1.Customers;  
  
    ```  
  
## Implementando a funcionalidade de salvar  
 Por padrão, o botão de salvar não está habilitado e a funcionalidade de salvar não está implementada.  Além disso, o código não será automaticamente adicionado para salvar dados modificados no banco de dados quando os controles associados a dados forem criados para fontes de dados de objeto.  Essa seção explica como habilitar o botão de salvar e implementar a funcionalidade de salvar para objetos [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
#### Para implementar a funcionalidade de salvar  
  
1.  Abrir Form1 na exibição Design.  
  
2.  Selecione o botão de salvar no **CustomerBindingNavigator** \(o botão com o ícone de disquete\).  
  
3.  Na janela **Propriedades**, defina a propriedade **Habilitado** como **True**.  
  
4.  Clique duas vezes no botão de salvar para criar um manipulador de eventos e alternar para o Editor de Códigos.  
  
5.  Adicione o código a seguir no manipulador de eventos do botão de salvar:  
  
    ```vb#  
    NorthwindDataContext1.SubmitChanges()  
    ```  
  
    ```c#  
    northwindDataContext1.SubmitChanges();  
    ```  
  
## Substituindo o comportamento padrão para realizar atualizações \(inserções, atualizações e exclusões\)  
  
#### Para substituir o comportamento padrão de atualização  
  
1.  Abra o arquivo LINQ to SQL no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  \(Clique duas vezes no arquivo **Northwind.dbml** no **Gerenciador de Soluções**.\)  
  
2.  Em **Gerenciador de Servidores**\/**Database Explorer**, expanda o nó **Stored Procedures** de bancos de dados Northwind e localize os procedimentos armazenados **InsertCustomers**, **UpdateCustomers** e **DeleteCustomers**.  
  
3.  Arraste os três procedimentos armazenados para o [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Os procedimentos armazenados são adicionados ao painel dos métodos como métodos <xref:System.Data.Linq.DataContext>.  Para obter mais informações, consulte [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md).  
  
4.  Selecione a classe de entidade **Customer** no [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
5.  Na janela **Propriedades**, selecione a propriedade **Insert**.  
  
6.  Clique nas reticências \(...\) ao lado de **Usar tempo de execução** para abrir a caixa de diálogo **Configurar Comportamento**.  
  
7.  Selecione **Personalizar**.  
  
8.  Selecione o método **InsertCustomers** na lista **Personalizar**.  
  
9. Clique em **Aplicar** para salvar a configuração para a Classe e o Comportamento selecionados.  
  
    > [!NOTE]
    >  Você pode continuar a configurar o comportamento para cada combinação de classe\/comportamento quando você clica em **Aplicar** depois de cada alteração.  Se você alterar a classe ou o comportamento antes de clicar em **Aplicar**, uma caixa de diálogo de aviso com uma oportunidade de aplicar as alterações será exibida.  
  
10. Selecione **Atualizar** na lista **Comportamento**.  
  
11. Selecione **Personalizar**.  
  
12. Selecione o método **UpdateCustomers** na lista **Personalizar**.  
  
     Inspecione a lista de **Argumentos de Método** e de **Propriedades de Classe** e observe que há dois **Argumentos de Método** e duas **Propriedades de Classe** para algumas colunas na tabela.  Isso facilita controlar as alterações e criar as instruções que conferem a existência de violações de simultaneidade.  
  
13. Mapeie o argumento do método **Original\_CustomerID** para a propriedade de classe **CustomerID \(Original\)**.  
  
    > [!NOTE]
    >  Por padrão, os argumentos do método mapearão para as propriedades da classe quando os nomes corresponderem.  Se os nomes de propriedade forem modificados e não corresponderem entre a tabela e a classe de entidade, você poderá ter que selecionar a propriedade da classe equivalente para a qual mapear se o Designer Relacional de Objetos não puder determinar o mapeamento correto.  Além disso, se os argumentos do método não tiverem propriedades da classe válidas para a qual mapear, você poderá definir o valor de **Propriedades de Classe** como **\(Nenhum\)**.  
  
14. Clique em **Aplicar** para salvar a configuração para a Classe e o Comportamento selecionados.  
  
15. Selecione **Excluir** na lista **Comportamento**.  
  
16. Selecione **Personalizar**.  
  
17. Selecione o método **DeleteCustomers** na lista **Personalizar**.  
  
18. Mapeie o argumento do método **Original\_CustomerID** para a propriedade de classe **CustomerID \(Original\)**.  
  
19. Clique em **OK**.  
  
> [!NOTE]
>  Embora isso não seja um problema para essa explicação passo a passo específica, vale observar que o [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] manipula automaticamente os valores gerados por banco de dados para as colunas identidade \(incremento automático\), rowguidcol \(GUID gerado por banco de dados\) e carimbo de data\/hora durante inserções e atualizações.  Os valores gerados pelo banco de dados em outros tipos de coluna resultarão inesperadamente em um valor nulo.  Para retornar os valores gerados por banco de dados, defina manualmente <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> como `true` e <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> como um dos seguintes: <xref:System.Data.Linq.Mapping.AutoSync>, <xref:System.Data.Linq.Mapping.AutoSync> ou <xref:System.Data.Linq.Mapping.AutoSync>.  
  
## Testando o aplicativo  
 Execute o aplicativo novamente para verificar se o procedimento armazenado **UpdateCustomers** atualiza corretamente o registro do cliente no banco de dados.  
  
#### Para testar o aplicativo  
  
1.  Pressione F5.  
  
2.  Modifique um registro na grade para testar o comportamento de atualização.  
  
3.  Adicione um novo registro para testar o comportamento de inserção.  
  
4.  Clique no botão de salvar para salvar as alterações de volta para o banco de dados.  
  
5.  Feche o formulário.  
  
6.  Pressione F5 e verifique se o registro atualizado e o registro inserido recentemente persistiram.  
  
7.  Exclua o novo registro que você criou na etapa 3 para testar o comportamento de exclusão.  
  
8.  Clique no botão de salvar para enviar as alterações e remova o registro excluído do banco de dados  
  
9. Feche o formulário.  
  
10. Pressione F5 e verifique se o registro excluído foi removido do banco de dados.  
  
    > [!NOTE]
    >  Se seu aplicativo usar o SQL Server Express Edition, dependendo do valor da propriedade **Copiar para Diretório de Saída** do arquivo de banco de dados, as alterações podem não aparecer quando você pressiona F5 na etapa 10.  Para obter mais informações, consulte [Como gerenciar arquivos de dados locais no projeto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
## Próximas etapas  
 Dependendo dos seus requisitos do aplicativo, há várias etapas que você pode querer realizar depois de criar as classes de entidade do [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  Entre algumas das melhorias que você pode fazer neste aplicativo estão:  
  
-   Implementar verificação de simultaneidade durante atualizações.  Para obter informações, consulte [Optimistic Concurrency: Overview](../Topic/Optimistic%20Concurrency:%20Overview.md).  
  
-   Adicionar consultas LINQ para filtrar dados.  Para obter informações, consulte [Introdução a consultas LINQ \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Consulte também  
 [LINQ to SQL Tools no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [LINQ to SQL Queries](../Topic/LINQ%20to%20SQL%20Queries.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Como: atribuir procedimentos armazenados para executar atualizações, inserções e exclusões \(Object Relational Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Novidades para desenvolvimento de aplicativos de dados no Visual Studio 2012](http://msdn.microsoft.com/pt-br/3d50d68f-5f44-4915-842f-6d42fce793f1)