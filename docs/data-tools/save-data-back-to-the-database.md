---
title: "Salvar dados no banco de dados | Microsoft Docs"
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
  - "conjuntos de dados [Visual Basic], validando dados"
  - "validação de dados, conjuntos de dados"
  - "salvamento de dados [Visual Studio]"
  - "versão da linha"
  - "atualizando conjuntos de dados, restrições"
  - "conjuntos de dados [Visual Basic], sobre conjuntos de dados"
  - "conjuntos de dados [Visual Basic], mesclando"
  - "atualizações, restrições em conjuntos de dados"
  - "salvando dados sobre como salvar dados"
  - "conjuntos de dados [Visual Basic], restrições"
  - "TableAdapters"
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
caps.latest.revision: 27
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Salvar dados no banco de dados
O conjunto de dados é uma cópia dos dados na memória. Se você modificar esses dados, você talvez queira salvar essas alterações no banco de dados. Você fazer isso de uma das três maneiras:  
  
-   chamando um dos `Update` métodos de um TableAdapter  
  
-   chamando um dos métodos DBDirect do TableAdapter.  
  
-   chamando o método UpdateAll no `TableAdapterManager` que o Visual Studio gera para você quando o conjunto de dados contém tabelas que estão relacionadas a outras tabelas no dataset.  
  
 Quando você vincular dados em tabelas do conjunto de dados a controles em um Windows Form ou página XAML, a arquitetura de ligação de dados faz todo esse trabalho para você.  
  
 Se você estiver familiarizado com os adaptadores de tabela, você pode ir diretamente para um destes tópicos:  
  
|Tópico|Descrição|  
|------------|---------------|  
|[Como inserir novos registros em um banco de dados](../data-tools/insert-new-records-into-a-database.md)|Como realizar atualizações e inserções usando TableAdapters ou objetos de comando|  
|[Como atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)|Como realizar atualizações com TableAdapters.|  
|[Atualização hierárquica](../data-tools/hierarchical-update.md)|Como executar atualizações de um dataset com duas ou mais tabelas relacionadas.|  
|[Instruções passo a passo: identificando uma exceção de simultaneidade](../data-tools/handle-a-concurrency-exception.md)|Como manipular exceções quando dois usuários tentam alterar os mesmos dados em um banco de dados ao mesmo tempo.|  
|[Como salvar dados usando uma transação](../data-tools/save-data-by-using-a-transaction.md)|Como salvar dados em uma transação usando o namespace System. Transactions e o objeto TransactionScope|  
|[Instruções passo a passo: salvando dados em uma transação](../data-tools/save-data-in-a-transaction.md)|Como salvar dados em uma transação usando o namespace System. Transactions.|  
|[Instruções passo a passo: salvando dados em um banco de dados \(várias tabelas\)](../data-tools/save-data-to-a-database-multiple-tables.md)|Como editar registros e salvar alterações em várias tabelas no banco de dados.|  
|[Como salvar dados de um objeto em um banco de dados](../data-tools/save-data-from-an-object-to-a-database.md)|Como passar dados de um objeto que não está em um conjunto de dados para um banco de dados usando um método TableAdapter DbDirect.|  
|[Instruções passo a passo: salvando dados com os métodos DBDirect TableAdapter](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|Como usar o TableAdapter para enviar consultas SQL diretamente para o banco de dados.|  
|[Como salvar um conjunto de dados como XML](../data-tools/save-a-dataset-as-xml.md)|Como salvar um conjunto de dados em um documento XML.|  
  
## Atualizações de dois estágios  
 Atualizar uma fonte de dados é um processo de duas etapas. A primeira etapa é atualizar o conjunto de dados com novos registros, registros alterados ou registros excluídos. Se seu aplicativo nunca envia essas alterações para a fonte de dados, terá concluído a atualização.  
  
 Se você enviar as alterações no banco de dados, uma segunda etapa é necessária. Se você não estiver usando controles ligados a dados, você precisa chamar o método Update do mesmo TableAdapter \(ou adaptador de dados\) que você usou para preencher o dataset, embora também possa usar adaptadores diferentes, por exemplo, para mover dados de uma fonte de dados para outro ou para atualizar várias fontes de dados manualmente. Se você não estiver usando a ligação de dados e está salvando alterações para tabelas relacionadas, você precisa criar manualmente uma variável da classe TableAdapterManager gerado automaticamente e chame seu método UdpateAll.  
  
 ![Atualizações de Dataset do Visual Basic](~/data-tools/media/vbdatasetupdates.gif "vbDatasetUpdates")  
Processo de atualização de dois estágios e a função do DataRowVersion em uma atualização bem\-sucedida  
  
 Um conjunto de dados contém coleções de tabelas, que contêm uma coleção de linhas. Ao adicionar ou remover linhas, se você pretende atualizar uma fonte de dados subjacente, você deve usar os métodos na propriedade DataTable.DataRowCollection. Esses métodos executam o controle de alterações necessário para atualizar a fonte de dados. Se você chamar a coleção RemoveAt na propriedade de linhas, a exclusão não ser comunicada de volta para o banco de dados.  
  
## Mesclar conjuntos de dados  
 Você pode atualizar o conteúdo de um conjunto de dados por *mesclando* \-lo com outro conjunto de dados. Isso envolve a cópia de conteúdo uma *fonte* conjunto de dados para o dataset chamado \(conhecido como o *destino* conjunto de dados\). Quando você mescla datasets, novos registros na fonte do dataset são adicionados ao conjunto de dados de destino. Além disso, colunas extras do DataSet fonte são adicionadas ao conjunto de dados de destino. Mesclar conjuntos de dados é útil quando você tem um conjunto de dados local e obter um segundo conjunto de dados de outro aplicativo ou de um componente como um serviço Web XML, ou quando você precisa integrar dados de vários conjuntos de dados.  
  
 Ao mesclar conjuntos de dados, você pode passar um argumento booleano \(`preserveChanges`\) que informa o <xref:System.Data.DataSet.Merge%2A> método se deseja manter modificações existentes no conjunto de dados de destino. Como datasets mantêm várias versões de registros, é importante ter em mente que mais de uma versão dos registros está sendo mesclada. A tabela a seguir ilustra um registro em dois conjuntos de dados que serão mesclados:  
  
|DataRowVersion|Conjunto de dados de destino|Conjunto de dados de origem|  
|--------------------|----------------------------------|---------------------------------|  
|Original|James Wilson|James C. Wilson|  
|Atual|Jim Wilson|James C. Wilson|  
  
 Chamar o <xref:System.Data.DataSet.Merge%2A> método na tabela acima com `preserveChanges=false targetDataset.Merge(sourceDataset)` resulta no seguinte:  
  
|DataRowVersion|Conjunto de dados de destino|Conjunto de dados de origem|  
|--------------------|----------------------------------|---------------------------------|  
|Original|James C. Wilson|James C. Wilson|  
|Atual|James C. Wilson|James C. Wilson|  
  
 Chamar o <xref:System.Data.DataSet.Merge%2A> método com `preserveChanges = true targetDataset.Merge(sourceDataset, true)` resulta no seguinte:  
  
|DataRowVersion|Conjunto de dados de destino|Conjunto de dados de origem|  
|--------------------|----------------------------------|---------------------------------|  
|Original|James C. Wilson|James C. Wilson|  
|Atual|Jim Wilson|James C. Wilson|  
  
> [!CAUTION]
>  No `preserveChanges = true` cenário, se o <xref:System.Data.DataSet.RejectChanges%2A> método for chamado em um registro no conjunto de dados de destino, em seguida, ele reverterá para os dados originais do *fonte* conjunto de dados. Isso significa que se você tentar atualizar a fonte de dados original com o conjunto de dados de destino, não é possível localizar a linha original para atualizar. Você pode impedir uma violação simultânea preenchendo outro dataset com os registros atualizados da fonte de dados e, em seguida, executar uma mesclagem impedindo uma violação de simultaneidade. \(Uma violação simultânea ocorre quando outro usuário modifica um registro na fonte de dados depois que o conjunto de dados tenha sido preenchido.\)  
  
## Restrições de atualização  
 Para fazer alterações em uma linha de dados existente, você adiciona ou atualiza dados nas colunas individuais. Se o dataset contiver restrições \(como chaves estrangeiras ou restrições não anuláveis\), é possível que você atualize um registro — depois de terminar de atualizar uma coluna, mas antes de chegar à próxima — o registro pode temporariamente estar em um estado de erro.  
  
 Para evitar violações de restrição você pode suspender temporariamente as restrições de atualização. Isso tem duas finalidades:  
  
-   Ela impede que um erro que está sendo gerada quando você atualiza uma coluna antes de obter a outra coluna.  
  
-   Ele suspende determinada atualização eventos sejam gerados \(eventos que são freqüentemente usados para validação\).  
  
 Depois de concluir uma atualização, você pode reativar restrição de verificação, que também reativa eventos de atualização e os aumenta.  
  
> [!NOTE]
>  No Windows Forms, a arquitetura de associação de dados construída dentro do datagrid suspende a restrição de verificação até que o foco é movido para fora de uma linha, e você não precisa chamar explicitamente o <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A> ou <xref:System.Data.DataRow.CancelEdit%2A> métodos.  
  
 As restrições são automaticamente desativado quando o <xref:System.Data.DataSet.Merge%2A> método é invocado em um conjunto de dados. Quando a mesclagem for concluída, se houver quaisquer restrições no conjunto de dados não pode ser habilitado, um <xref:System.Data.ConstraintException> é lançada. Nessa situação, o <xref:System.Data.DataSet.EnforceConstraints%2A> está definida como `false` e todas as violações de restrição devem ser resolvidas antes de redefinir o <xref:System.Data.DataSet.EnforceConstraints%2A> propriedade `true`.  
  
 Depois de concluir uma atualização, você pode reativar restrição de verificação, que também reativa eventos de atualização e os aumenta.  
  
 Para obter mais informações sobre a suspensão de eventos, consulte [Desativar restrições ao preencher um conjunto de dados](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
## Erros de atualização de conjunto de dados  
 Quando você atualiza um registro em um dataset, há a possibilidade de um erro. Por exemplo, você pode inadvertidamente gravar dados em uma coluna que é do tipo de dados errado ou muito longo, ou que tenha algum outro problema de integridade. Ou você pode ter verificações de validação específicas do aplicativo que podem gerar erros personalizados durante qualquer estágio de um evento de atualização. Para obter mais informações, consulte [Validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md).  
  
## Manter informações sobre alterações  
 Informações sobre as alterações em um dataset são mantidas de duas maneiras: sinalizando a linha que indica se ele foi alterado \(<xref:System.Data.DataRow.RowState%2A>\) e mantendo várias cópias de um registro \(<xref:System.Data.DataRowVersion>\). Usando essas informações, processos podem determinar o que foi alterado no dataset e podem enviar atualizações apropriadas para a fonte de dados.  
  
### Propriedade RowState  
 O <xref:System.Data.DataRow.RowState%2A> propriedade de uma <xref:System.Data.DataRow> objeto é um valor que fornece informações sobre o status de uma linha específica de dados.  
  
 A tabela a seguir detalha os possíveis valores a <xref:System.Data.DataRowState> enumeração:  
  
|Valor de DataRowState|Descrição|  
|---------------------------|---------------|  
|<xref:System.Data.DataRowState>|A linha foi adicionada como um item para um <xref:System.Data.DataRowCollection>. \(Uma linha nesse estado não tem uma versão original correspondente desde que não existia no momento a última <xref:System.Data.DataRow.AcceptChanges%2A> método foi chamado\).|  
|<xref:System.Data.DataRowState>|A linha foi excluída usando o <xref:System.Data.DataRow.Delete%2A> de um <xref:System.Data.DataRow> objeto.|  
|<xref:System.Data.DataRowState>|A linha foi criada, mas não é parte de qualquer <xref:System.Data.DataRowCollection>. Um <xref:System.Data.DataRow> objeto está nesse estado imediatamente após ele ter sido criado antes de ser adicionado a uma coleção, ou se ele tiver sido removido de uma coleção.|  
|<xref:System.Data.DataRowState>|Um valor de coluna na linha foi alterado de alguma forma.|  
|<xref:System.Data.DataRowState>|A linha não foi alterada desde <xref:System.Data.DataRow.AcceptChanges%2A> foi chamado pela última vez.|  
  
### Enumeração DataRowVersion  
 DataSets mantêm várias versões de registros. O <xref:System.Data.DataRowVersion> enumeração de uma <xref:System.Data.DataRow> objeto é um valor que pode ser usado para retornar uma versão específica de um <xref:System.Data.DataRow> objeto.  
  
 A tabela a seguir detalha os possíveis valores a <xref:System.Data.DataRowVersion> enumeração:  
  
|Valor de DataRowVersion|Descrição|  
|-----------------------------|---------------|  
|<xref:System.Data.DataRowVersion>|A versão atual de um registro contém todas as modificações executadas no registro desde a última vez <xref:System.Data.DataRow.AcceptChanges%2A> foi chamado. Se a linha foi excluída não há nenhuma versão atual.|  
|<xref:System.Data.DataRowVersion>|O valor padrão de um registro, conforme definido pela fonte de dados ou esquema de conjunto de dados.|  
|<xref:System.Data.DataRowVersion>|A versão original de um registro é uma cópia do registro como ele nas últimas alterações foram confirmadas no conjunto de dados. Em termos práticos, isso é normalmente a versão de um registro como lida de uma fonte de dados.|  
|<xref:System.Data.DataRowVersion>|A versão proposta de um registro que está disponível temporariamente, enquanto você está no meio de uma atualização — ou seja, entre o momento você chamou o <xref:System.Data.DataRow.BeginEdit%2A> método e o <xref:System.Data.DataRow.EndEdit%2A> método. Você normalmente acessa a versão proposta de um registro em um manipulador para um evento, como <xref:System.Data.DataTable.RowChanging>. Chamar o <xref:System.Data.DataRow.CancelEdit%2A> método reverte as alterações e exclui a versão proposta da linha de dados.|  
  
 As versões originais e atuais são úteis quando informações de atualização são transmitidas para uma fonte de dados. Normalmente, quando uma atualização é enviada para a fonte de dados, as novas informações para o banco de dados estão na versão atual de um registro. Informações da versão original são usadas para localizar o registro para atualizar. Por exemplo, em um caso onde a chave primária de um registro é alterada, você deve ter uma maneira de localizar o registro adequado na fonte de dados, para atualizar as alterações. Se nenhuma versão original existisse, o registro provavelmente seria anexado à fonte de dados, resultando não apenas em um registro extra indesejado, mas em um registro que está impreciso e desatualizado. As duas versões também são usadas no controle de simultaneidade; Você pode comparar a versão original contra um registro na fonte de dados para determinar se o registro tiver sido alterado desde que foi carregado para o dataset.  
  
 A versão proposta é útil quando você precisa realizar validação antes de realmente confirmar as alterações para o conjunto de dados.  
  
 Mesmo se os registros foram alterados, não há sempre versões originais ou atuais de linha. Quando você insere uma nova linha na tabela, não há nenhuma versão original, somente a versão atual. Da mesma forma, se você excluir uma linha, chamando a tabela `Delete` método, há uma versão original, mas nenhuma versão atual.  
  
 Você pode testar para ver se uma versão específica de um registro existe consultando uma linha de dados <xref:System.Data.DataRow.HasVersion%2A> método. Você pode acessar tanto a versão de um registro, passando um <xref:System.Data.DataRowVersion> valor de enumeração como um argumento opcional quando você solicita o valor de uma coluna.  
  
## Obter registros alterados  
 É comum que você não atualize cada registro em um conjunto de dados. Por exemplo, um usuário pode estar trabalhando com um Windows Forms <xref:System.Windows.Forms.DataGridView> controle que exibe vários registros. No entanto, o usuário pode atualizar apenas alguns registros, excluir um e inserir um novo. Conjuntos de dados e tabelas de dados fornecem um método \(`GetChanges`\) para retornar somente as linhas que foram modificadas.  
  
 Você pode criar subconjuntos de registros alterados usando o `GetChanges` método da tabela de dados \(<xref:System.Data.DataTable.GetChanges%2A>\) ou do conjunto de dados \(<xref:System.Data.DataSet.GetChanges%2A>\) em si. Se você chamar o método para a tabela de dados, ela retornará uma cópia da tabela com apenas os registros alterados. Da mesma forma, se você chamar o método no conjunto de dados, você terá um novo dataset com apenas registros alterados nele.`GetChanges` por si só retornará todos os registros alterados. Em contraste, passando o desejado <xref:System.Data.DataRowState> como um parâmetro para o `GetChanges` método, você pode especificar o subconjunto de registros alterados que você deseja: recém\-adicionados registros, registros marcados para exclusão, registros separados, ou registros modificados.  
  
 Obter um subconjunto de registros alterados é útil quando você deseja enviar registros para outro componente para processamento. Em vez de enviar todo o conjunto de dados, você pode reduzir a sobrecarga de se comunicar com o outro componente por meio somente os registros que o componente precisa. Para obter mais informações, consulte [Como recuperar linhas alteradas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  
  
## Confirmando alterações no conjunto de dados  
 Como as alterações são feitas no conjunto de dados, o <xref:System.Data.DataRow.RowState%2A> propriedade das linhas alteradas é definida. As versões originais e atuais de registros são estabelecidas e mantidas e disponibilizadas para você pelo <xref:System.Data.DataRowView.RowVersion%2A> propriedade. Os metadados armazenados nessas propriedades representam as alterações é necessário para enviar as atualizações adequadas para a fonte de dados.  
  
 Se as alterações refletem o estado atual da fonte de dados, você não precisa manter essas informações. Normalmente, há duas vezes quando o conjunto de dados e sua fonte estão em sincronia:  
  
-   Imediatamente após você ter carregado informações para o conjunto de dados, como quando você lê dados da fonte.  
  
-   Após enviar alterações do dataset para a fonte de dados \(mas não antes, porque você pode perder as informações necessárias para enviar alterações para o banco de dados\).  
  
 Você pode confirmar as alterações pendentes para o conjunto de dados chamando o <xref:System.Data.DataSet.AcceptChanges%2A> método. Normalmente, <xref:System.Data.DataSet.AcceptChanges%2A> seria chamado nos seguintes momentos em seu aplicativo.  
  
-   Depois que você carregar o conjunto de dados. Se você carregar um dataset chamando um TableAdapter `Fill` método, então o adaptador confirma automaticamente as alterações para você. No entanto, se você carregar um dataset, mesclando outro dataset para ele, em seguida, você precisa confirmar as alterações manualmente.  
  
    > [!NOTE]
    >  Você pode impedir que o adaptador confirme automaticamente as alterações ao chamar o `Fill` método definindo o `AcceptChangesDuringFill` propriedade do adaptador de `false`. Se ele for definido como `false`, o <xref:System.Data.DataRow.RowState%2A> de cada linha inserida durante o preenchimento é definido como <xref:System.Data.DataRowState>.  
  
-   Após você ter enviado alterações do dataset para outro processo, como um serviço Web XML.  
  
    > [!CAUTION]
    >  Confirmar a alteração dessa maneira apaga qualquer mudança da informação. Confirme alterações até depois de realizar qualquer operação na qual seu aplicativo depende em saber quais alterações foram feitas no conjunto de dados.  
  
 Esse método realiza o seguinte:  
  
-   Grava o <xref:System.Data.DataRowVersion> versão de um registro em seu <xref:System.Data.DataRowVersion> versão, substituindo a versão original.  
  
-   Remove qualquer linha cuja <xref:System.Data.DataRow.RowState%2A> está definida como <xref:System.Data.DataRowState>.  
  
-   Conjuntos de <xref:System.Data.DataRow.RowState%2A> propriedade de um registro para <xref:System.Data.DataRowState>.  
  
 O <xref:System.Data.DataSet.AcceptChanges%2A> método está disponível em três níveis. Você pode chamá\-lo em uma <xref:System.Data.DataRow> objeto, que confirma as alterações apenas naquela linha. Você também pode chamá\-lo em uma <xref:System.Data.DataTable> objeto para confirmar todas as linhas em uma tabela, ou o <xref:System.Data.DataSet> objeto para confirmar todas as alterações pendentes em todos os registros de todas as tabelas do conjunto de dados.  
  
 A tabela a seguir descreve quais alterações são confirmadas com base em qual objeto que o método é chamado no.  
  
|Método|Resultado|  
|------------|---------------|  
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|As alterações são confirmadas somente sobre a linha específica|  
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|As alterações são confirmadas em todas as linhas na tabela específica|  
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|As alterações são confirmadas em todas as linhas em todas as tabelas do conjunto de dados|  
  
> [!NOTE]
>  Se você carregar um dataset chamando um TableAdapter `Fill` método, você não tem que explicitamente aceitar alterações; por padrão o `Fill` chamadas de método de `AcceptChanges` método quando ele tiver terminado de preencher a tabela de dados.  
  
 Um método relacionado, `RejectChanges`, desfaz o efeito das alterações copiando o <xref:System.Data.DataRowVersion> versão volta para o <xref:System.Data.DataRowVersion> versão de registros e definindo o <xref:System.Data.DataRow.RowState%2A> de cada registro de volta para <xref:System.Data.DataRowState>.  
  
## Validação de dados  
 Para verificar se os dados em seu aplicativo atendem aos requisitos dos processos que é passado para, geralmente você precisa adicionar validação. Isso pode envolver verificação que uma entrada do usuário em um formulário está correta, validação de dados enviados ao seu aplicativo por outro aplicativo, ou mesmo verificar que informações calculadas no seu componente fica dentro das restrições dos dados fonte e requisitos do aplicativo.  
  
 Você pode validar dados de várias maneiras:  
  
-   Na camada comercial, adicionando código ao seu aplicativo para validar dados. O conjunto de dados é um local que você pode fazer isso. O dataset fornece algumas das vantagens de validação back\-end — como a capacidade para validar alterações como valores de coluna e linha estão mudando. Para obter mais informações, consulte [Validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md).  
  
-   Na camada de apresentação, adicionando validação a formulários. Para obter mais informações, consulte [Validação da entrada do usuário no Windows Forms](../Topic/User%20Input%20Validation%20in%20Windows%20Forms.md).  
  
-   Nos dados de back\-end, enviando dados para a fonte de dados — por exemplo, o banco de dados — e permitindo que ele aceite ou rejeite os dados. Se você estiver trabalhando com um banco de dados que tem recursos sofisticados para validação de dados e fornecer informações de erro, isso pode ser uma abordagem prática porque você pode validar os dados, independentemente de onde ele vem. No entanto, ele pode não acomodar requisitos de validação específicas do aplicativo. Além disso, ter a fonte de dados validar dados pode resultar em várias viagens à fonte de dados, dependendo de como seu aplicativo facilita em resolver erros de validação gerados pelo back\-end.  
  
    > [!IMPORTANT]
    >  Ao usar comandos de dados com um <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> definida como <xref:System.Data.CommandType>, cuidadosamente verifique informações que são enviadas de um cliente antes de passá\-la para seu banco de dados. Usuários mal\-intencionados podem tentar enviar \(injetar\) instruções SQL modificadas ou adicionais em um esforço para obter acesso não autorizado ou danificar o banco de dados. Antes de você transferir a entrada do usuário para um banco de dados, você sempre deve verificar se as informações são válidas; é uma prática recomendada sempre usar consultas parametrizadas ou procedimentos armazenados quando possível. Para obter mais informações, consulte [Script Exploits Overview](../Topic/Script%20Exploits%20Overview.md).  
  
 Depois que as alterações foram feitas em um dataset, você pode transmitir as alterações para uma fonte de dados. Mais comumente, você faz isso chamando o `Update` método de um TableAdapter \(ou adaptador de dados\). O método loops a cada registro em uma tabela de dados, determina que tipo de atualização é necessário \(atualizar, inserir ou excluir\), se houver e, em seguida, executa o comando apropriado.  
  
## Como uma atualização é transmitida para a fonte de dados  
 Como uma ilustração de como as atualizações são feitas, suponha que seu aplicativo usa um conjunto de dados que contém uma única tabela de dados. O aplicativo busca duas linhas do banco de dados. Após a recuperação, a tabela de dados na memória tem esta aparência:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Unchanged)    c400         Nancy Buchanan    Pending  
```  
  
 Seu aplicativo altera o status de Nancy Buchanan para "Preferred". Como resultado dessa alteração, o valor da <xref:System.Data.DataRow.RowState%2A> propriedade daquela linha muda de <xref:System.Data.DataRowState> para <xref:System.Data.DataRowState>. O valor de <xref:System.Data.DataRow.RowState%2A> propriedade para a primeira linha permanece <xref:System.Data.DataRowState>. A tabela de dados agora é semelhante a:  
  
```  
(RowState)     CustomerID   Name             Status  
(Unchanged)    c200         Robert Lyon      Good  
(Modified)     c400         Nancy Buchanan    Preferred  
```  
  
 Seu aplicativo agora chama o `Update` método para transmitir o dataset para o banco de dados. O método inspeciona cada linha por sua vez. Para a primeira linha, o método não transmite instrução SQL para o banco de dados, porque essa linha não foi alterada desde que ela foi originalmente procurada no banco de dados.  
  
 Para a segunda linha, no entanto, o `Update` método automaticamente chama o comando de dados adequado e o transmite para o banco de dados. A sintaxe específica da instrução SQL depende do dialeto do SQL suportado para o armazenamento de dados subjacente. Mas as seguintes características gerais da instrução SQL transmitida devem ser observadas:  
  
-   A instrução SQL transmitida é uma instrução UPDATE. O adaptador sabe para usar uma instrução UPDATE porque o valor de <xref:System.Data.DataRow.RowState%2A> é de propriedade <xref:System.Data.DataRowState>.  
  
-   A instrução SQL transmitida inclui uma cláusula WHERE indicando que o destino da instrução UPDATE é a linha cujo `CustomerID = 'c400'`. Esta parte da declaração SELECT distingue a linha de destino de todas as outras porque o `CustomerID` é a chave primária da tabela de destino. As informações para a cláusula WHERE são derivadas da versão original do registro \(`DataRowVersion.Original`\), caso os valores necessários para identificar a linha que foi alterada.  
  
-   A instrução SQL transmitida inclui a cláusula SET, para definir os novos valores das colunas modificadas.  
  
    > [!NOTE]
    >  Se o TableAdapter `UpdateCommand` propriedade foi definida para o nome de um procedimento armazenado, o adaptador não constrói uma instrução SQL. Em vez disso, ele chama o procedimento armazenado com os parâmetros apropriados passados.  
  
## Passando parâmetros  
 Valores de registros a serem atualizados no banco de dados são passados usando parâmetros. Quando o TableAdapter `Update` método executa uma instrução UPDATE, ele precisa preencher os valores de parâmetro. Ele obtém esses valores do `Parameters` coleta para o comando de dados apropriados — neste caso, o `UpdateCommand` objeto no TableAdapter.  
  
 Se você usou as ferramentas do Visual Studio para gerar um adaptador de dados, o `UpdateCommand` objeto conterá uma coleção de parâmetros que corresponde a cada espaço reservado de parâmetro na instrução.  
  
 O <xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> propriedade de cada parâmetro aponta para uma coluna na tabela de dados. Por exemplo, o `SourceColumn` propriedade para o `au_id` e `Original_au_id` parâmetros é definida como qualquer coluna na tabela de dados que contém a identificação do autor. Quando o adaptador `Update` método é executado, ele lê o autor coluna id do registro sendo atualizado e preenche os valores na instrução.  
  
 Em uma instrução UPDATE, você precisa especificar novos valores \(aqueles que serão gravados no registro\), bem como os antigos valores \(para que o registro a ser atualizado possa ser localizado no banco de dados\). Portanto, há dois parâmetros para cada valor: um para a cláusula SET e um diferente para a cláusula WHERE. Ambos os parâmetros lêem dados do registro sendo atualizado, mas eles obtêm versões diferentes do valor da coluna com base no parâmetro de [SourceVersion Property](https://msdn.microsoft.com/en-us/library/system.data.sqlclient.sqlparameter.sourceversion.aspx). O parâmetro para a cláusula SET obtém a versão atual e o parâmetro para a cláusula WHERE obtém a versão original.  
  
> [!NOTE]
>  Você também pode definir valores `Parameters` coleção por conta própria no código, que normalmente você faria em um manipulador de eventos para o adaptador de dados <xref:System.Data.DataTable.RowChanging> eventos.  
  
## Consulte também  
 [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md)   
 [Como atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Visão geral de aplicativos de dados no Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectando a dados no Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)