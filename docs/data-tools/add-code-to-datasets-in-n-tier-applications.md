---
title: "Adicionar c&#243;digo ao datasets em aplicativos de n camadas | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "aplicativos de n camadas, estendendo conjuntos de dados"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adicionar c&#243;digo ao datasets em aplicativos de n camadas
Você pode estender a funcionalidade de um dataset, criando um arquivo de classe parcial para o dataset e adicionar código a ele \(em vez de adicionar o código para o  *DatasetName*.Arquivo de DataSet.Designer\).  \(Classes parciais permitem codificar uma classe específica para ser dividida entre arquivos físicos múltiplos.  Para obter mais informações, consulte [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [Classes e métodos partial](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
 O código que define um DataSet é gerado sempre que forem feitas alterações a definição de conjunto de dados \(na caixa [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)\).  Esse código também é gerado quando alterações são feitas durante a execução de qualquer assistente que modifica a configuração de .  Para impedir que seu código seja excluído durante a regeneração do dataset, adicione código para o dataset do arquivo de classe parcial.  
  
 By default, after you separate the dataset and `TableAdapter` code, the result is a discrete class file in each project.  O projeto original tem um arquivo chamado  DatasetName. Designer.vb \(ou  DatasetName. Designer.cs\) que contém o código `TableAdapter`.  O projeto designado na caixa  **Projeto DataSet**  propriedade tem um arquivo chamado  *DatasetName* . DataSet.Designer.vb \(ou  DatasetName. DataSet.Designer.cs\) que contém o código de dataset.  
  
> [!NOTE]
>  Quando você separar DataSets e `TableAdapter` s \(definindo o  **DataSet Project**  Propriedade\), classes parciais DataSet existentes no projeto não serão movidas automaticamente.  Classes parciais DataSet existente devem ser movidas manualmente para o projeto DataSet.  
  
> [!NOTE]
>  O [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md) também fornece funcionalidade para gerar <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> manipuladores de eventos quando código de validação deve ser adicionado.  Para obter mais informações, consulte [Adicionar validação a um conjunto de dados de n camadas](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### Como: adicionar código ao Datasets em aplicativos N\-Tier  
  
1.  Localize o projeto que contém o arquivo .xsd \([Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Clique duas vezes no arquivo **.xsd** para abrir o [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Clique com o botão direito do mouse o tabela de dados para o qual você deseja adicionar código \(o nome da tabela na barra de título\) e clique em  **Exibir código** .  
  
     Um classe parcial é criado e abre no Editor de Códigos.  
  
4.  Adicione um código de usuário dentro da declaração de classe parcial.  
  
     O exemplo a seguir mostra onde adicionar código para o CustomersDataTable in a NorthwindDataSet:  
  
    ```vb#  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```c#  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## Consulte também  
 [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)   
 [Adicionar código a TableAdapters em aplicativos de n camadas](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Visão geral de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Visão geral de atualização hierárquica](../Topic/Hierarchical%20Update%20Overview.md)   
 [Criando aplicativos de dados](../data-tools/creating-data-applications.md)   
 [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)