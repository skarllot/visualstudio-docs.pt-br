---
title: "Ferramentas do conjunto de dados no Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.DataSet"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "conjuntos de dados não tipados"
  - "conjuntos de dados [Visual Basic], propriedades estendidas"
  - "conjuntos de dados tipados"
  - "registro atual no conjunto de dados"
  - "XML [Visual Basic], conjuntos de dados"
  - "Classe de conjunto de dados, sobre conjuntos de dados"
  - "restrições exclusivas (conjuntos de dados)"
  - "relacionamentos de dados"
  - "registros pai em conjuntos de dados"
  - "propriedades estendidas, em datasets tipados"
  - "conjuntos de dados [Visual Basic]"
  - "esquemas [Visual Basic], conjuntos de dados"
  - "conjuntos de dados [Visual Basic] msprop"
  - "tabelas de detalhes mestre, conjuntos de dados"
  - "bancos de dados [Visual Basic], atualizando"
  - "msprop"
  - "chaves estrangeiras, conjuntos de dados"
  - "Classe DataSet"
  - "conjuntos de dados [Visual Basic], preenchendo"
  - "maiúsculas e minúsculas, conjuntos de dados"
  - "restrições [Visual Basic], conjuntos de dados"
  - "registros filho"
  - "tabelas relacionadas, conjuntos de dados"
  - "atualizando conjuntos de dados, sobre atualizações de conjunto de dados"
  - "dados em cache, conjuntos de dados"
  - "Objeto DataRelation, conjuntos de dados"
  - "datasets não digitados, em comparação a datasets tipados"
  - "cache [Visual Studio], conjuntos de dados"
  - "conjuntos de dados [Visual Basic], relações"
  - "tabelas relacionadas"
  - "Esquemas XML, sobre esquemas XML e conjuntos de dados"
  - "relações, conjuntos de dados"
  - "conjuntos de dados tipados, em comparação com conjuntos de dados não tipados"
  - "conjuntos de dados [Visual Basic], preenchendo"
  - "conjuntos de dados [Visual Basic] namespace"
  - "adaptadores de dados, preenchendo conjuntos de dados"
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 49
caps.handback.revision: 39
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ferramentas do conjunto de dados no Visual Studio
> [!NOTE]
>  Conjuntos de dados e classes relacionadas são herdadas tecnologias .NET no início dos anos 2000 que permitem que aplicativos trabalhar com dados na memória enquanto estiver desconectado do banco de dados. Eles são especialmente úteis para aplicativos que permitem que os usuários modifiquem dados e manter as alterações no banco de dados. Embora Datasets provaram para ser uma tecnologia muito bem\-sucedida, é recomendável que novos aplicativos .NET usam o Entity Framework. O Entity Framework fornece uma forma mais natural para trabalhar com dados tabulares como modelos de objeto e tem uma interface de programação mais simples.  
  
 Um conjunto de dados é um objeto de memória que é essencialmente um banco de dados simplificado. Ele contém objetos DataTable, DataRow e de DataColumn em que você pode armazenar e modificar dados de um ou mais bancos de dados sem a necessidade de manter uma conexão aberta.  O conjunto de dados mantém informações sobre alterações em seus dados, portanto, as atualizações podem ser rastreadas e enviadas de volta para o banco de dados quando seu aplicativo se torna reconectado.  
  
 Conjuntos de dados e classes relacionadas são definidos no namespace System. Data na biblioteca de classes do .NET Framework. Você pode criar e modificar conjuntos de dados dinamicamente no código; Para obter mais informações sobre como fazer isso, consulte ADO.NET. A documentação nesta seção mostra como trabalhar com conjuntos de dados com designers do Visual Studio. Uma coisa a saber: conjuntos de dados feitos com os designers usam TableAdapters para interagir com o banco de dados, enquanto os conjuntos de dados feitas por meio de programação usar DataAdapters. Para obter informações em Criando conjuntos de dados programaticamente, consulte [DataAdapters e DataReaders](../Topic/DataAdapters%20and%20DataReaders.md)  
  
 Se seu aplicativo só precisa ler dados de um banco de dados e não executar atualizações, adiciona ou exclui, geralmente pode obter um melhor desempenho usando um DataReader para recuperar dados em uma lista genérica ou outro objeto de coleção. Se você estiver exibindo os dados, você pode vincular dados a interface do usuário à coleção.  
  
## Fluxos de trabalho do conjunto de dados  
 O Visual Studio fornece muitas ferramentas para simplificar o trabalho com conjuntos de dados. O fluxo de trabalho de ponta a ponta básico é:  
  
-   Use a janela de fonte de dados para criar um novo conjunto de dados de uma ou mais fontes de dados. Use o Designer de conjunto de dados para configurar o conjunto de dados e definir suas propriedades. Por exemplo, você precisa especificar quais tabelas da fonte de dados para incluir e quais colunas de cada tabela. Escolha cuidadosamente reduzir a quantidade de memória que exigirá que o conjunto de dados. Consulte [Criar e configurar conjuntos de dados](../data-tools/create-and-configure-datasets-in-visual-studio.md).  
  
-   Especifica as relações entre as tabelas para que as chaves estrangeiras são tratadas corretamente. Consulte [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
-   Use o Assistente de configuração do TableAdapter para especificar a consulta ou procedimento armazenado que preencherá o conjunto de dados, e quais operações de banco de dados \(update, delete e assim por diante\) para implementar. Consulte estes tópicos:  
  
    -   [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)  
  
    -   [Editar dados em conjuntos de dados](../data-tools/edit-data-in-datasets.md)  
  
    -   [Validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md)  
  
    -   [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)  
  
-   Consultar e pesquisar os dados no conjunto de dados. Consulte [Conjuntos de dados de consulta](../data-tools/query-datasets.md).[!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] permite [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md) sobre os dados em um <xref:System.Data.DataSet> objeto. Para obter mais informações, consulte [LINQ to DataSet](../Topic/LINQ%20to%20DataSet.md).  
  
-   Use a janela fontes de dados para associar controles de interface do usuário para o conjunto de dados ou suas colunas individuais e especifique quais colunas são editáveis pelo usuário. Consulte [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Arquitetura de conjuntos de dados e de N camadas  
 Para obter informações sobre conjuntos de dados em aplicativos de N camadas, consulte [Trabalhar com conjuntos de dados em aplicativos de n camadas](../data-tools/work-with-datasets-in-n-tier-applications.md)  
  
## DataSets e XML  
 Para obter informações sobre a conversão de conjuntos de dados para e do XML, consulte [Ler dados XML em um dataset](../data-tools/read-xml-data-into-a-dataset.md) e [Como salvar um conjunto de dados como XML](../data-tools/save-a-dataset-as-xml.md).  
  
## Consulte também  
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)