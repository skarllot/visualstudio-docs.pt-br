---
title: "Validar dados em conjuntos de dados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataTable.ColumnChanging"
  - "System.Data.DataTable.ColumnChanging"
  - "System.Data.DataTable.RowChanging"
  - "DataTable.RowChanging"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "validação de dados, conjuntos de dados"
  - "validação de dados"
  - "validação de dados, conjuntos de dados"
  - "atualizando conjuntos de dados, validação de dados"
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 24
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Validar dados em conjuntos de dados
Validação de dados é o processo que confirma que os valores sendo inseridos em objetos de dados de acordo com as restrições no esquema do dataset, bem como as regras estabelecidas para seu aplicativo. Validar dados antes de enviar atualizações para o banco de dados subjacente é uma boa prática que reduz erros bem como o número potencial de processamentos entre um aplicativo e o banco de dados. Você pode confirmar que os dados estão sendo gravados para um conjunto de dados são válidos criando verificações de validação para o próprio dataset. O conjunto de dados pode verificar os dados, independentemente de como a atualização está sendo executada — se diretamente pelos controles em um formulário, de um componente, ou de alguma outra maneira. Como o conjunto de dados é parte do seu aplicativo, é um local lógico para criar validação específica do aplicativo \(diferente de criar as mesmas verificações no back\-end do banco de dados\).  
  
 O local sugerido para adicionar validação para o aplicativo é um arquivo de classe parcial do dataset. Em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], abra o **DataSet Designer** e clique duas vezes na coluna ou tabela que você deseja criar a validação. Esta ação cria automaticamente um <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> manipulador de eventos. Para obter mais informações, consulte [Como validar dados durante alterações em coluna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md), ou [Como validar dados durante alterações de linha](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md). Para obter um exemplo completo, consulte [Instruções passo a passo: adicionando validação a um conjunto de dados](../Topic/Walkthrough:%20Adding%20Validation%20to%20a%20Dataset.md).  
  
## Validando dados  
 Validação em um conjunto de dados pode ser realizada:  
  
-   Criando sua própria validação específica do aplicativo que pode verificar dados durante alterações em valores em uma coluna de dados individuais. Para obter mais informações, consulte [Como validar dados durante alterações em coluna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   Criando sua própria validação específica do aplicativo que pode verificar dados durante alterações em valores enquanto um inteiro de dados está mudando a linha. Para obter mais informações, consulte [Como validar dados durante alterações de linha](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
-   Ao criar chaves, restrições exclusivas, e assim por diante como parte da definição do esquema real do conjunto de dados. Para obter mais informações sobre incorporar validação na definição de esquema, consulte [Restringir uma Coluna para conter valores exclusivos](../Topic/How%20to:%20Add%20Columns%20to%20a%20DataTable.md#SpecifyUniqueConstraint).  
  
-   Definindo o <xref:System.Data.DataColumn> Propriedades do objeto, como <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, e <xref:System.Data.DataColumn.Unique%2A>.  
  
 Há vários eventos que são gerados pelo <xref:System.Data.DataTable> quando uma alteração está ocorrendo em um registro de objeto:  
  
-   O <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventos são gerados durante e após cada alteração em uma coluna individual. O <xref:System.Data.DataTable.ColumnChanging> evento é útil quando você deseja validar alterações em colunas específicas. Informações sobre a alteração proposta são passadas como um argumento com o evento. Para obter mais informações, consulte [Como validar dados durante alterações em coluna](../Topic/How%20to:%20Validate%20Data%20During%20Column%20Changes.md).  
  
-   O <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventos são gerados durante e após qualquer alteração em uma linha. O <xref:System.Data.DataTable.RowChanging> evento é mais geral, porque ele simplesmente indica que uma alteração está ocorrendo em algum lugar na linha; você não souber qual coluna foi alterada. Para obter mais informações, consulte [Como validar dados durante alterações de linha](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
 Por padrão, cada alteração em uma coluna, portanto, gera quatro eventos: primeiro o <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventos para a coluna específica que está sendo alterada e, em seguida, o <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventos. Se várias alterações estão sendo feitas para a linha, os eventos serão gerados para cada alteração.  
  
> [!NOTE]
>  A linha de dados <xref:System.Data.DataRow.BeginEdit%2A> método desativa o <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventos após cada alteração de coluna individual. Nesse caso, o evento não é gerado até que o <xref:System.Data.DataRow.EndEdit%2A> método foi chamado, quando a <xref:System.Data.DataTable.RowChanging> e <xref:System.Data.DataTable.RowChanged> eventos são gerados apenas uma vez. Para obter mais informações, consulte [Desativar restrições ao preencher um conjunto de dados](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 O evento que você escolhe depende de como granular você deseja que seja a validação. Se for importante que você capture um erro imediatamente quando uma coluna é alterada, crie validação usando o <xref:System.Data.DataTable.ColumnChanging> evento. Caso contrário, use o <xref:System.Data.DataTable.RowChanging> evento, que pode resultar em captura de vários erros ao mesmo tempo. Além disso, se seus dados são estruturados de forma que o valor de uma coluna é validado com base no conteúdo de outra coluna, você deve executar a validação durante o <xref:System.Data.DataTable.RowChanging> evento.  
  
 Quando registros são atualizados, o <xref:System.Data.DataTable> objeto gera eventos que você pode responder enquanto alterações estão ocorrendo e depois que forem feitas alterações.  
  
 Se seu aplicativo estiver usando um dataset tipado, você pode criar manipuladores de eventos com rigidez de tipos. Isso adicionará quatro eventos tipados que você pode criar manipuladores; `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, and `dataTableNameRowDeleted`. Esses manipuladores de eventos tipados passam um argumento que inclui os nomes de coluna da tabela que tornam o código que mais fácil de escrever e ler.  
  
## Eventos de atualização de dados  
  
|Evento|Descrição|  
|------------|---------------|  
|<xref:System.Data.DataTable.ColumnChanging>|O valor em uma coluna está sendo alterado. O evento passa a linha e coluna para você, juntamente com o novo valor proposto.|  
|<xref:System.Data.DataTable.ColumnChanged>|O valor em uma coluna foi alterado. O evento passa a linha e coluna para você, juntamente com o valor proposto.|  
|<xref:System.Data.DataTable.RowChanging>|As alterações feitas em uma <xref:System.Data.DataRow> objeto estão prestes a serem confirmadas de volta para o conjunto de dados. Se você não tiver chamado o <xref:System.Data.DataRow.BeginEdit%2A> método, o <xref:System.Data.DataTable.RowChanging> é gerado para cada alteração em uma coluna, imediatamente após o <xref:System.Data.DataTable.ColumnChanging> evento foi gerado. Se você chamou <xref:System.Data.DataRow.BeginEdit%2A> antes de fazer alterações, o <xref:System.Data.DataTable.RowChanging> é gerado somente quando você chamar o <xref:System.Data.DataRow.EndEdit%2A> método.<br /><br /> O evento passa a linha para você e um valor que indica o tipo de ação \(alterar, inserir e assim por diante\) está sendo executado.|  
|<xref:System.Data.DataTable.RowChanged>|Uma linha foi alterada. O evento passa a linha para você e um valor que indica o tipo de ação \(alterar, inserir e assim por diante\) está sendo executado.|  
|<xref:System.Data.DataTable.RowDeleting>|Uma linha está sendo excluída. O evento passa a linha para você e um valor que indica o tipo de ação \(excluir\) está sendo executado.|  
|<xref:System.Data.DataTable.RowDeleted>|Uma linha foi excluída. O evento passa a linha para você e um valor que indica o tipo de ação \(excluir\) está sendo executado.|  
  
 O <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, e <xref:System.Data.DataTable.RowDeleting> são gerados durante o processo de atualização. Você pode usar esses eventos para validar dados ou executar outros tipos de processamento. Como as atualizações estão em processo durante esses eventos, você pode cancelar a atualização lançando uma exceção, que impede que a alteração seja concluída.  
  
 O <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged>, e <xref:System.Data.DataTable.RowDeleted> eventos são eventos de notificação que são gerados quando a atualização foi concluída com êxito. Esses eventos são úteis quando você deseja fazer outra ação com base em uma atualização bem\-sucedida.  
  
## Validar dados durante alterações de coluna  
  
> [!NOTE]
>  O **Dataset Designer** cria uma classe parcial onde lógica de validação pode ser adicionada a um conjunto de dados. O dataset gerado pelo designer não excluirá ou alterar qualquer código na classe parcial.  
  
 Você pode validar dados quando o valor em uma coluna de dados é alterado respondendo ao <xref:System.Data.DataTable.ColumnChanging> evento. Quando gerado, esse evento passa um argumento do evento \(<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>\) que contém o valor sendo proposto para a coluna atual. Com base no conteúdo de `e.ProposedValue`, você pode:  
  
-   Aceite o valor proposto, sem fazer nada.  
  
-   Rejeitar o valor proposto, definindo o erro da coluna \(<xref:System.Data.DataRow.SetColumnError%2A>\) de dentro do manipulador de eventos de alteração de coluna.  
  
-   Se desejar usar um <xref:System.Windows.Forms.ErrorProvider> controle para exibir uma mensagem de erro para o usuário. Para obter mais informações, consulte [Componente ErrorProvider](../Topic/ErrorProvider%20Component%20\(Windows%20Forms\).md).  
  
 A validação também pode ser executada durante o <xref:System.Data.DataTable.RowChanging> evento. Para obter mais informações, consulte [Como validar dados durante alterações de linha](../Topic/How%20to:%20Validate%20Data%20During%20Row%20Changes.md).  
  
## Validar dados durante alterações de linha  
 Você pode escrever código para verificar se cada coluna que você deseja validar contém dados que atenda aos requisitos do seu aplicativo. Se o valor proposto é inaceitável, defina a coluna para indicar que ele contém um erro. Os exemplos a seguir definem um erro de coluna quando a `Quantity` coluna é 0 ou menos. Os manipuladores de eventos de alteração de linha devem se parecer com os exemplos a seguir.  
  
#### Para validar dados quando uma linha altera \(Visual Basic\)  
  
1.  Abra o dataset no **Dataset Designer**. Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Clique duas vezes a barra de título da tabela que você deseja validar. Esta ação cria automaticamente o <xref:System.Data.DataTable.RowChanging> manipulador de eventos do <xref:System.Data.DataTable> no arquivo de classe parcial do dataset.  
  
    > [!TIP]
    >  Clique duas vezes à esquerda do nome da tabela para criar o manipulador de eventos de alteração de linha. Se você clicar duas vezes no nome da tabela, você pode editar o nome da tabela.  
  
     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]  
  
#### Para validar dados quando uma linha altera \(c\#\)  
  
1.  Abra o dataset no **Dataset Designer**. Para obter mais informações, consulte [Como abrir um conjunto de dados no Designer de Conjunto de Dados](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Clique duas vezes a barra de título da tabela que você deseja validar. Essa ação cria um arquivo de classe parcial para o <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    >  O **Dataset Designer** não cria automaticamente um manipulador de eventos para o <xref:System.Data.DataTable.RowChanging> evento. Você precisa criar um método para manipular o <xref:System.Data.DataTable.RowChanging> eventos e executar o código para ligar o evento no método de inicialização da tabela.  
  
3.  Copie o código a seguir na classe parcial:  
  
    ```  
    public override void EndInit()  
    {  
        base.EndInit();  
        Order_DetailsRowChanging += TestRowChangeEvent;  
    }  
  
    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)  
    {  
        if ((short)e.Row.Quantity <= 0)  
        {  
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
        }  
        else  
        {  
            e.Row.SetColumnError("Quantity", "");  
        }  
    }  
    ```  
  
## Para recuperar linhas alteradas  
 Cada linha em uma tabela de dados tem uma <xref:System.Data.DataRow.RowState%2A> que controla o estado atual da linha, usando os valores na propriedade de <xref:System.Data.DataRowState> enumeração. Você pode retornar linhas alteradas de uma dataset ou tabela de dados chamando o `GetChanges` método de um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable>. Você pode verificar se existem alterações antes de chamar `GetChanges` chamando o <xref:System.Data.DataSet.HasChanges%2A> método de um conjunto de dados. Para obter mais informações sobre <xref:System.Data.DataSet.HasChanges%2A>, consulte [Como verificar linhas alteradas](../Topic/How%20to:%20Check%20for%20Changed%20Rows.md).  
  
> [!NOTE]
>  Após confirmar alterações em uma dataset ou tabela de dados \(chamando o <xref:System.Data.DataSet.AcceptChanges%2A> método\), o `GetChanges` método não retornará dados. Se seu aplicativo precisar processar linhas alteradas, você deve fazer isso antes de chamar o `AcceptChanges` método.  
  
 Chamar o <xref:System.Data.DataSet.GetChanges%2A> método de um conjunto de dados ou tabela de dados retorna uma novo dataset ou uma tabela que contém somente os registros que foram alterados. Se você quiser obter somente registros específicos — por exemplo, somente registros novos ou somente registros modificados — você pode passar um valor da <xref:System.Data.DataRowState> enumeração como um parâmetro para o `GetChanges` método.  
  
 Use o <xref:System.Data.DataRowVersion> enumeração para acessar as versões diferentes de uma linha \(por exemplo, convém examinar os valores originais em uma linha antes de processá\-la.  
  
#### Para obter todos os registros alterados de um conjunto de dados  
  
-   Chamar o <xref:System.Data.DataSet.GetChanges%2A> método de um conjunto de dados.  
  
     O exemplo a seguir cria um novo dataset chamado `changedRecords` e a preenche com todos os registros alterados do outro dataset chamado `dataSet1`.  
  
     [!CODE [VbRaddataEditing#14](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#14)]  
  
#### Para obter todos os registros alterados de uma tabela de dados  
  
-   Chamar o <xref:System.Data.DataTable.GetChanges%2A> método de um DataTable.  
  
     O exemplo a seguir cria uma nova tabela de dados chamada `changedRecordsTable` e a preenche com todos os registros alterados de outra tabela de dados chamada `dataTable1`.  
  
     [!CODE [VbRaddataEditing#15](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#15)]  
  
#### Para obter todos os registros que têm um estado de linha específico  
  
-   Chamar o `GetChanges` método de um conjunto de dados ou tabela de dados e passe um <xref:System.Data.DataRowState> valor de enumeração como um argumento.  
  
     O exemplo a seguir mostra como criar um novo dataset chamado `addedRecords` e preenchê\-lo somente com registros que foram adicionados para o `dataSet1` conjunto de dados.  
  
     [!CODE [VbRaddataEditing#16](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#16)]  
  
-   O exemplo a seguir mostra como retornar todos os registros adicionados recentemente para o `Customers` tabela:  
  
     [!CODE [VbRaddataEditing#17](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#17)]  
  
## Acessar a versão Original de um DataRow  
 Quando forem feitas alterações em linhas de dados, o conjunto de dados manterá tanto o original \(<xref:System.Data.DataRowVersion>\) e novos \(<xref:System.Data.DataRowVersion>\) versões da linha. Por exemplo, antes de chamar o `AcceptChanges` método, seu aplicativo pode acessar as versões diferentes de um registro \(conforme definido no <xref:System.Data.DataRowVersion> enumeração\) e processar as alterações de acordo.  
  
> [!NOTE]
>  Versões diferentes de uma linha existem somente após ela ter sido editada e antes que tenha tido a `AcceptChanges` método chamado. Após o `AcceptChanges` método foi chamado, as versões atuais e originais são as mesmas.  
  
 Passando o <xref:System.Data.DataRowVersion> valor junto com o índice da coluna \(ou nome da coluna como uma cadeia de caracteres\) retorna o valor da versão de linha específica da coluna. A coluna alterada é identificada durante a <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.ColumnChanged> eventos, portanto, que é um bom momento para inspecionar a diferença linha versões para fins de validação. No entanto, se você temporariamente suspenso restrições, esses eventos não serão gerados e você precisará programaticamente identificar quais colunas foram alteradas. Você pode fazer isso, iterando através de <xref:System.Data.DataTable.Columns%2A> coleta e comparando os diferentes <xref:System.Data.DataRowVersion> valores.  
  
#### Para obter a versão original de um registro  
  
-   Acessar o valor de uma coluna passando o <xref:System.Data.DataRowVersion> da linha que você deseja retornar.  
  
     O exemplo a seguir mostra como você pode usar um <xref:System.Data.DataRowVersion> valor para obter o valor original de um `CompanyName` campo um <xref:System.Data.DataRow>:  
  
     [!CODE [VbRaddataEditing#21](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#21)]  
  
## Acessar a versão atual de um DataRow  
  
#### Para obter a versão atual de um registro  
  
-   Acessar o valor de uma coluna e adicione um parâmetro ao índice que indica qual versão de uma linha que você deseja retornar.  
  
     O exemplo a seguir mostra como você pode usar um <xref:System.Data.DataRowVersion> valor para obter o valor atual de um `CompanyName` campo um <xref:System.Data.DataRow>:  
  
     [!CODE [VbRaddataEditing#22](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#22)]  
  
## Consulte também  
 [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)   
 [Como conectar a dados em um banco de dados](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Como validar dados no controle DataGridView dos Windows Forms](../Topic/How%20to:%20Validate%20Data%20in%20the%20Windows%20Forms%20DataGridView%20Control.md)   
 [Como exibir ícones de erro para validação do formulário com o componente ErrorProvider dos Windows Forms](../Topic/How%20to:%20Display%20Error%20Icons%20for%20Form%20Validation%20with%20the%20Windows%20Forms%20ErrorProvider%20Component.md)