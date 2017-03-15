---
title: "Como: preencher um dataset com dados | Microsoft Docs"
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
  - "TableAdapter.GetData"
  - "TableAdapter.Fill"
  - "conjuntos de dados [Visual Basic], preenchendo"
  - "Objetos DataTable, carregando"
  - "dados [Visual Basic], carregando em conjuntos de dados"
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como: preencher um dataset com dados
A frase "preenchendo um dataset com dados" se refere a carregar dados para os objetos individuais <xref:System.Data.DataTable> que compõem o DataSet.  Você preenche as tabelas de dados executando consultas do TableAdapter ou executando comandos do adaptador de dados \(por exemplo, <xref:System.Data.SqlClient.SqlDataAdapter>\) .  
  
 Se você deve usar TableAdapters ou adaptadores de dados depende de como você criou o DataSet.  Se você usou as ferramentas de design no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como o [Assistente para Configuração da Fonte de Dados](../data-tools/media/data-source-configuration-wizard.png), seu dataset contém TableAdapters.  Para obter mais informações sobre TableAdapters, consulte [Visão geral de TableAdapter](../data-tools/tableadapter-overview.md).  Se você criou o DataSet programaticamente, será necessário criar adaptadores de dados para carregar dados nas tabelas de dados.  
  
> [!NOTE]
>  Ao arrastar itens da [Janela Fontes de Dados](../Topic/Data%20Sources%20Window.md) para um formulário, o código para preencher a tabela de dados com dados é adicionado automaticamente para o manipulador de eventos `Form_Load`.  Abra o formulário no code editor para ver a sintaxe exata para preencher as suas tabelas específicas.  Se você não desejar preencher a tabela quando o formulário é carregado, mova este código para algum outro método, ou remova\-o totalmente.  
  
## Preenchendo um DataSet usando um TableAdapter  
 Você pode chamar uma consulta no TableAdapter para carregar dados em tabelas de dados em um DataSet.  Passe o <xref:System.Data.DataTable> que você deseja preencher para a consulta do TableAdapter.  Se sua consulta usa parâmetros, passe\-os para o método.  Se o DataSet conter várias tabelas, você deve ter TableAdapters separados para cada tabela e portanto deve preencher cada tabela separadamente.  
  
> [!NOTE]
>  Por padrão, sempre que você executa uma consulta do TableAdapter, os dados na tabela são desmarcados antes dos resultados da consulta que está sendo carregado na tabela.  Você pode manter os dados existentes na tabela e anexar os resultados configurando a propriedade `ClearBeforeFill` do TableAdapter para `false`.  
  
#### Para preencher um DataSet com dados usando um TableAdapter  
  
1.  Abra seu formulário ou componente no **Code Editor**.  
  
2.  Adicione código em qualquer lugar em seu aplicativo onde você precisa carregar uma tabela de dados com dados.  Se sua consulta não aceita parâmetros, passe na <xref:System.Data.DataTable> que você deseja preencher.  O código deve ser semelhante ao seguinte:  
  
     [!code-cs[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_1.vb)]  
  
3.  Se sua consulta usa parâmetros, passe a <xref:System.Data.DataTable> que você deseja preencher e os parâmetros esperados pela consulta.  Dependendo dos parâmetros atuais em sua consulta, o código deve ser semelhante aos exemplos a seguir:  
  
     [!code-cs[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_2.vb)]  
  
## Preenchendo um DataSet usando um DataAdapter  
 Você chama o método `Fill` do adaptador de dados.  Isso faz com que o adaptador execute a instrução SQL ou o procedimento armazenado referenciado na sua propriedade `SelectCommand` e coloca os resultados em uma tabela no DataSet.  Se o DataSet contém várias tabelas, você deve ter adaptadores de dados separados para cada tabela e portanto deve preencher cada tabela separadamente.  
  
#### Para preencher um DataSet com dados usando um DataAdapter  
  
-   Chame o método <xref:System.Data.Common.DataAdapter.Fill%2A> do <xref:System.Data.Common.DataAdapter>, passando o <xref:System.Data.DataSet> ou a <xref:System.Data.DataTable> para carregar os dados.  Por exemplo:  
  
     [!code-cs[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/CSharp/how-to-fill-a-dataset-with-data_3.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../data-tools/codesnippet/VisualBasic/how-to-fill-a-dataset-with-data_3.vb)]  
  
     Geralmente você deve fornecer o nome da <xref:System.Data.DataTable> para carregar os dados.  Se você passar o nome de um <xref:System.Data.DataSet> em vez de uma tabela de dados específica, uma <xref:System.Data.DataTable> denominada `Table1` é adicionada ao dataset e carregada com os resultados do banco de dados \(em oposição a carregar os dados em um <xref:System.Data.DataTable> existente no dataset\).  Para obter mais informações, consulte [Populando um DataSet a partir de um DataAdapter](../Topic/Populating%20a%20DataSet%20from%20a%20DataAdapter.md).  
  
## Consulte também  
 [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Buscando dados no aplicativo](../data-tools/fetching-data-into-your-application.md)   
 [Preparando o aplicativo para receber dados](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Editando dados no aplicativo](../data-tools/editing-data-in-your-application.md)   
 [Validando dados](../Topic/Validating%20Data.md)   
 [Salvando dados](../data-tools/saving-data.md)