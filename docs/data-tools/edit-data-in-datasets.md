---
title: "Editar dados em conjuntos de dados | Microsoft Docs"
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
  - "conjuntos de dados [Visual Basic] editando dados"
  - "dados [Visual Studio], editando em conjuntos de dados"
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Editar dados em conjuntos de dados
Editar os dados em tabelas de dados tanto quanto você edita os dados em uma tabela em qualquer banco de dados — o processo pode incluir inserir, atualizar e excluir registros na tabela. Em um formulário de associação de dados, você pode especificar quais campos são editáveis pelo usuário. Nesses casos, a infra\-estrutura de ligação de dados lida com todo o controle de alterações para que as alterações podem ser enviadas no banco de dados posteriormente. Se você programaticamente fazer edições em dados e quiser enviar essas alterações no banco de dados, você deve usar os objetos e métodos que o controle de alterações para você.  
  
 Além de alterar os dados reais, você também pode consultar um <xref:System.Data.DataTable> para retornar linhas específicas dos dados, por exemplo, linhas individuais, versões específicas de linhas \(original e proposta\), somente linhas que foram alteradas e linhas que possuem erros.  
  
## Editar linhas em um conjunto de dados  
 Para editar uma linha existente em um <xref:System.Data.DataTable>, você precisa localizar o <xref:System.Data.DataRow> você deseja editar e, em seguida, atribuir os valores atualizados para as colunas desejadas.  
  
 Se você não souber o índice da linha você deseja editar, use o `FindBy` método para pesquisar a chave primária.  
  
 [!CODE [VbRaddataEditing#3](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#3)]  
  
 Se você souber o índice da linha, você pode acessar e edita linhas como esta:  
  
 [!CODE [VbRaddataEditing#5](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#5)]  
  
## Inserir uma nova linha em um dataset  
 Aplicativos que usam controles vinculados a dados normalmente adicionam novos registros através do botão "Adicionar novo" em um [controle BindingNavigator](../Topic/BindingNavigator%20Control%20\(Windows%20Forms\).md).  
  
 Para adicionar manualmente novos registros em um conjunto de dados, crie uma nova linha de dados chamando o método na DataTable. Em seguida, adicione a linha a <xref:System.Data.DataRow> coleção \(<xref:System.Data.DataTable.Rows%2A>\) da <xref:System.Data.DataTable>  
  
 [!CODE [VbRaddataEditing#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#1)]  
  
 Para manter as informações que o dataset precisa para enviar atualizações para a fonte de dados, use o <xref:System.Data.DataRow.Delete%2A> método para remover linhas em uma tabela de dados. Por exemplo, se seu aplicativo usa um TableAdapter \(ou <xref:System.Data.Common.DataAdapter>\), o adaptador `Update` método excluirá as linhas no banco de dados que têm um <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState>.  
  
 Se seu aplicativo não precisa enviar atualizações de volta para uma fonte de dados, é possível remover registros acessando a coleção da linha de dados diretamente \(<xref:System.Data.DataRowCollection.Remove%2A>\).  
  
#### Para excluir registros de uma tabela de dados  
  
-   Chamar o <xref:System.Data.DataRow.Delete%2A> método de um <xref:System.Data.DataRow>.  
  
     Esse método não remove fisicamente o registro. em vez disso, ele marca o registro para exclusão.  
  
    > [!NOTE]
    >  Se você receber a propriedade count de um <xref:System.Data.DataRowCollection>, a contagem resultante inclui registros que foram marcados para exclusão. Para obter uma contagem precisa apenas de registros que não são marcados para exclusão, você pode fazer um loop através da coleção examinando o <xref:System.Data.DataRow.RowState%2A> propriedade de cada registro \(registros marcados para exclusão têm um <xref:System.Data.DataRow.RowState%2A> de <xref:System.Data.DataRowState>\). Como alternativa, você pode criar uma exibição de dados de um dataset que filtra com base no estado de linha e obter a propriedade count de lá.  
  
     O exemplo a seguir mostra como chamar o <xref:System.Data.DataRow.Delete%2A> método para marcar a primeira linha de `Customers` como excluída da tabela:  
  
     [!CODE [VbRaddataEditing#8](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#8)]  
  
## Determinar se há linhas alteradas  
 Quando forem feitas alterações a registros em um conjunto de dados, informações sobre essas alterações são armazenadas até confirmá\-las. As alterações são confirmadas ao chamar o `AcceptChanges` método de um conjunto de dados, tabela de dados ou chamar o `Update` método de um TableAdapter ou adaptador de dados.  
  
 As alterações são controladas em cada linha de dados de duas maneiras:  
  
-   Cada linha de dados contém informações sobre seu <xref:System.Data.DataRow.RowState%2A> \(por exemplo, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>\).  
  
-   Cada linha de dados alterada contém várias versões dessa linha \(<xref:System.Data.DataRowVersion>\); o original \(antes de alterações\) e versões atuais \(após alterações\) — que você pode acessar. Durante o período quando uma alteração é pendente \(o tempo que você pode responder a <xref:System.Data.DataTable.RowChanging> evento\), uma terceira versão — a versão proposta — também está disponível. Para obter mais informações, consulte [Como obter versões específicas de um DataRow](../Topic/How%20to:%20Get%20Specific%20Versions%20of%20a%20DataRow.md).  
  
 O <xref:System.Data.DataSet.HasChanges%2A> método de um dataset retorna `true` se alterações tiverem sido feitas no conjunto de dados. Após determinar que linhas alteradas existem, você pode chamar o `GetChanges` método de um <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> para retornar um conjunto de linhas alteradas. Para obter mais informações, consulte [Como recuperar linhas alteradas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  
  
#### Para determinar se as alterações foram feitas para quaisquer linhas  
  
-   Chamar o <xref:System.Data.DataSet.HasChanges%2A> método de um conjunto de dados para verificar linhas alteradas.  
  
     O exemplo a seguir mostra como verificar o valor de retorno de <xref:System.Data.DataSet.HasChanges%2A> método para detectar se há quaisquer linhas alteradas em um dataset chamado `NorthwindDataset1`.  
  
     [!CODE [VbRaddataEditing#12](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#12)]  
  
## Determinando o tipo de alterações  
 Você também pode verificar para ver quais tipos de alterações foram feitas em um dataset, passando um valor da <xref:System.Data.DataRowState> enumeração para o <xref:System.Data.DataSet.HasChanges%2A> método.  
  
#### Para determinar que tipo de alterações foram feitas em uma linha  
  
-   Passar um <xref:System.Data.DataRowState> de valor para o <xref:System.Data.DataSet.HasChanges%2A> método.  
  
     O exemplo a seguir mostra como verificar um dataset chamado `NorthwindDataset1` para determinar se tem havido quaisquer novas linhas adicionadas a ele:  
  
     [!CODE [VbRaddataEditing#13](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#13)]  
  
## Para localizar linhas com erros  
 Ao trabalhar com colunas individuais e linhas de dados, pode haver vezes que um registro contenha um erro. Você pode verificar o `HasErrors` para determinar se existem erros em um <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow>.  
  
1.  Verifique o `HasErrors` propriedade para ver se há erros no dataset.  
  
2.  Se o `HasErrors` é de propriedade `true`, interaja nas coleções de tabelas e, em seguida, as linhas para encontrar a linha com o erro.  
  
     [!CODE [VbRaddataEditing#23](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#23)]