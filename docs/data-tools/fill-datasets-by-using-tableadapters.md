---
title: "Preencher datasets usando TableAdapters | Microsoft Docs"
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
  - "conjuntos de dados [Visual Basic]"
  - "conjuntos de dados [Visual Basic], o carregamento de dados"
  - "recuperação de dados"
  - "recuperando dados"
  - "conjuntos de dados [Visual Basic], preenchendo"
  - "dados [Visual Studio], recuperando"
  - "dados [Visual Studio], conjuntos de dados"
ms.assetid: 55f3bfbe-db78-4486-add3-c62f49e6b9a0
caps.latest.revision: 32
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Preencher datasets usando TableAdapters
Um TableAdapter é o componente que preenche um DataSet com dados do banco de dados, com base em uma ou mais consultas ou procedimentos armazenados que você especificar. TableAdapters também pode executar adiciona, atualizações e exclusões no banco de dados para manter as alterações feitas ao conjunto de dados ou para emitir comandos globais não relacionados a qualquer tabela específica.  
  
> [!NOTE]
>  TableAdapters são geradas pelo designer do Visual Studio. Se você estiver criando conjuntos de dados programaticamente, use um DataAdapter, que é uma classe do .NET Framework.  
  
 Para obter informações detalhadas sobre as operações do TableAdapter, você pode pular diretamente para um destes tópicos:  
  
|Tópico|Descrição|  
|------------|---------------|  
|[Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)|Como usar os designers para criar e configurar TableAdapters.|  
|[Criar consultas TableAdapter parametrizadas](../data-tools/create-parameterized-tableadapter-queries.md)|Como habilitar usuários para fornecer argumentos para consultas ou procedimentos do TableAdapter.|  
|[Acessar diretamente o banco de dados com um TableAdapter](../data-tools/directly-access-the-database-with-a-tableadapter.md)|Como usar os métodos Dbdirect de um TableAdapter.|  
|[Desativar restrições ao preencher um conjunto de dados](../data-tools/turn-off-constraints-while-filling-a-dataset.md)|Como trabalhar com restrições de chave estrangeira quando a atualização de dados.|  
|[How to extend the functionality of a TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)|Como adicionar código personalizado a um TableAdapter.|  
|[Ler dados XML em um dataset](../data-tools/read-xml-data-into-a-dataset.md)|Como trabalhar com XML.|  
  
## Visão geral de TableAdapters  
 TableAdapters são componentes gerados pelo designer que se conectar a um banco de dados, executam consultas ou procedimentos armazenados e preencher seu DataTable com os dados retornados. TableAdapters também são usados para enviar dados atualizados de seu aplicativo de volta para o banco de dados. Você pode ter tantas consultas quanto você deseja em um TableAdapter desde que elas retornem dados de acordo com o esquema da tabela à qual o TableAdapter está associado. O diagrama a seguir mostra como os TableAdapters interagir com bancos de dados e outros objetos na memória:  
  
 ![Fluxo de dados em um aplicativo cliente](~/docs/data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Enquanto TableAdapters são criados com o **Dataset Designer**, as classes TableAdapter geradas não são geradas como classes aninhadas do <xref:System.Data.DataSet>. Eles estão localizados em um namespace separado específico para cada conjunto de dados. Por exemplo, se você tiver um dataset chamado `NorthwindDataSet`, os TableAdapters associados com a <xref:System.Data.DataTable>s no `NorthwindDataSet` no `NorthwindDataSetTableAdapters` namespace. Para acessar um determinado TableAdapter programaticamente, você deve declarar uma nova instância do TableAdapter. Por exemplo:  
  
 [!CODE [VbRaddataTableAdapters#7](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#7)]  
  
## Esquema de DataTable associados  
 Ao criar um TableAdapter, a consulta inicial ou procedimento armazenado é usado para definir o esquema do TableAdapter associado do <xref:System.Data.DataTable>. Você executa essa consulta inicial ou procedimento armazenado chamando o TableAdapter `Fill` método \(que preenche o TableAdapter associado do <xref:System.Data.DataTable>\). Todas as alterações feitas à consulta principal do TableAdapter são refletidas no esquema da tabela de dados associada. Por exemplo, remover uma coluna da consulta principal remove a coluna da tabela de dados associada. Se quaisquer consultas adicionais no TableAdapter usam instruções SQL retornando colunas que não estão na consulta principal, em seguida, o designer tentará sincronizar as alterações de coluna entre a consulta principal e quaisquer consultas adicionais. Para obter mais informações, consulte [Como editar TableAdapters](../Topic/How%20to:%20Edit%20TableAdapters.md).  
  
## Comandos de atualização do TableAdapter  
 A funcionalidade de atualização de um TableAdapter é dependente de quanta informação está disponível com base na consulta principal fornecida no TableAdapter Wizard. Por exemplo, TableAdapters que estejam configurados para buscar valores de várias tabelas \(JOINs\), valores escalares, exibições ou os resultados de funções de agregação não são criadas inicialmente com a capacidade de enviar atualizações de volta para o banco de dados subjacente. No entanto, você pode configurar os comandos INSERT, UPDATE e DELETE manualmente no **propriedades** janela.  
  
## Consultas TableAdapter  
 ![TableAdapter com múltiplas consultas](~/docs/data-tools/media/tableadapter.gif "TableAdapter")  
  
 TableAdapters podem conter consultas múltiplas para preencher suas tabelas de dados associados. Você pode definir tantas consultas para um TableAdapter quanto seu aplicativo requer, desde que cada consulta retorna dados de acordo com o mesmo esquema que sua tabela de dados associada. Isso permite o carregamento de dados que satisfaçam critérios diferentes. Por exemplo, se seu aplicativo contiver uma tabela de clientes, você pode criar uma consulta que preenche a tabela com todos os clientes cujo nome começa com uma letra específica e outra consulta que preenche a tabela com todos os clientes localizados no mesmo estado. Para preencher um `Customers` tabela com clientes em um estado determinado você pode criar um `FillByState` consulta que leva um parâmetro para o valor de estado: `SELECT * FROM Customers WHERE State = @State`. Você executa a consulta chamando o `FillByState` método e passando o valor do parâmetro assim: `CustomerTableAdapter.FillByState("WA")`.  
  
 Além de consultas que retornam dados do mesmo esquema como tabela de dados do TableAdapter, você pode adicionar consultas que retornam valores escalares de \(único\). Por exemplo, criar uma consulta que retorna uma contagem de clientes \(`SELECT Count(*) From Customers`\) é válido para um `CustomersTableAdapter` mesmo que os dados retornados não estão de acordo com o esquema da tabela.  
  
## Propriedade ClearBeforeFill  
 Por padrão, sempre que você executa uma consulta para preencher a tabela de dados do TableAdapter, os dados serão limpos e somente os resultados da consulta são carregados na tabela. Defina o TableAdapter `ClearBeforeFill` propriedade `false` se você deseja adicionar ou mesclar os dados retornados de uma consulta aos dados existentes em uma tabela de dados. Independentemente de você limpar os dados, você precisa explicitamente enviar atualizações de volta para o banco de dados, se desejado. Portanto, lembre\-se de salvar as alterações feitas nos dados na tabela antes de executar outra consulta que preenche a tabela. Para obter mais informações, consulte [Como atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## Herança do TableAdapter  
 TableAdapters estendem a funcionalidade dos adaptadores de dados padrão, encapsulando um configurado <xref:System.Data.Common.DataAdapter>. Por padrão, o TableAdapter herda de <xref:System.ComponentModel.Component> e não pode ser convertido para o <xref:System.Data.Common.DataAdapter> classe. Converter um TableAdapter para um <xref:System.Data.Common.DataAdapter> resulta em um <xref:System.InvalidCastException>. Para alterar a classe base de um TableAdapter, você pode digitar uma classe que deriva de <xref:System.ComponentModel.Component> no **classe Base** propriedade do TableAdapter no **Dataset Designer**.  
  
## Propriedades e métodos do TableAdapter  
 A classe TableAdapter não é parte do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], e assim você não pode procurar por ele na documentação ou **Pesquisador de objetos**. Ele é criado em tempo de design, quando você usa um dos assistentes mencionados acima. O nome atribuído a um TableAdapter quando você o cria baseia\-se no nome da tabela que você está trabalhando. Por exemplo, ao criar um TableAdapter com base em uma tabela em um banco de dados denominado `Orders`, o TableAdapter seria nomeado `OrdersTableAdapter`. O nome da classe do TableAdapter pode ser alterado usando o **nome** propriedade o **Dataset Designer**.  
  
 A seguir está as propriedades dos TableAdapters e métodos mais usados:  
  
|Membro|Descrição|  
|------------|---------------|  
|`TableAdapter.Fill`|Preenche a tabela de dados associada ao TableAdapter com os resultados do comando SELECT do TableAdapter.|  
|`TableAdapter.Update`|Envia as alterações no banco de dados e retorna um inteiro que representa o número de linhas afetadas pela atualização. Para obter mais informações, consulte [Como atualizar dados usando um TableAdapter](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Retorna um novo <xref:System.Data.DataTable> preenchido com dados.|  
|`TableAdapter.Insert`|Cria uma nova linha na tabela de dados. Para obter mais informações, consulte [Como inserir novos registros em um banco de dados](../data-tools/insert-new-records-into-a-database.md).|  
|`TableAdapter.ClearBeforeFill`|Determina se uma tabela de dados é esvaziada antes de chamar um dos `Fill` métodos.|  
  
## Método Update do TableAdapter  
 TableAdapters usam comandos de dados para leitura e gravação do banco de dados. Inicial do TableAdapter `Fill` consulta \(principal\) é usada como base para criar o esquema da tabela de dados associada, bem como o `InsertCommand`, `UpdateCommand`, e `DeleteCommand` comandos associados a `TableAdapter.Update` método. Isso significa que chamar um TableAdapter `Update` método executa as instruções criadas quando o TableAdapter foi originalmente configurado, e não uma das consultas adicionais adicionada com o **Assistente de configuração de consulta do TableAdapter**.  
  
 Quando você usa um TableAdapter, ele efetivamente executa as mesmas operações com os comandos que você geralmente deseja executar. Por exemplo, quando você chamar o adaptador `Fill` método, o adaptador executa o comando de dados no seu `SelectCommand` propriedade e usa um leitor de dados \(por exemplo, <xref:System.Data.SqlClient.SqlDataReader>\) para carregar o resultado na tabela de dados. Da mesma forma, quando você chamar o adaptador `Update` método, ele executa o comando apropriado \(no `UpdateCommand`, `InsertCommand`, e `DeleteCommand` Propriedades\) para cada registro alterado na tabela de dados.  
  
> [!NOTE]
>  Se não houver informações suficientes na consulta principal, o `InsertCommand`, `UpdateCommand`, e `DeleteCommand` comandos são criados por padrão quando o TableAdapter é gerado. Se principal do TableAdapter consulta é mais de uma instrução SELECT de tabela simples, é possível que o designer não será capaz de gerar o `InsertCommand`, `UpdateCommand`, e `DeleteCommand`. Se esses comandos não são gerados, você pode receber um erro ao executar o `TableAdapter.Update` método.  
  
## GenerateDbDirectMethods do TableAdapter  
 Além de `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, TableAdapters são criados com métodos que podem ser executados diretamente no banco de dados. Esses métodos \(`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`\) podem ser chamados diretamente para manipular dados no banco de dados. Isso significa que você pode chamar esses métodos individuais no seu código em vez de chamar o TableAdapter para manipular as inserções, atualizações e exclusões pendentes para a tabela de dados associada.  
  
 Se você não deseja criar esses métodos diretos, defina o TableAdapter **GenerateDbDirectMethods** propriedade `false` \(no **propriedades** janela\). Consultas adicionais no TableAdapter são consultas autônomas — elas não geram esses métodos.  
  
## Suporte do TableAdapter para tipos anuláveis  
 Os TableAdapters oferecem suporte a tipos anuláveis `Nullable(Of T)` e `T?`. Para obter mais informações sobre tipos anuláveis em Visual Basic, consulte [Tipos de valor que permitem valor nulo](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types). Para obter mais informações sobre tipos anuláveis em c\#, consulte [Usando tipos anuláveis](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types).  
  
## Segurança  
 Ao usar comandos de dados com um `CommandType` definida como <xref:System.Data.CommandType>, cuidadosamente verifique informações que são enviadas de um cliente antes de passá\-la para seu banco de dados. Usuários mal\-intencionados podem tentar enviar \(injetar\) instruções SQL modificadas ou adicionais em um esforço para obter acesso não autorizado ou danificar o banco de dados. Antes de você transferir a entrada do usuário para um banco de dados, você sempre deve verificar se as informações são válidas. Uma prática recomendada é sempre usar consultas parametrizadas ou procedimentos armazenados quando possível.  
  
## Consulte também  
 [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)