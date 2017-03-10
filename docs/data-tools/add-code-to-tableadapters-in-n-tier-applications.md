---
title: "Adicionar c&#243;digo a TableAdapters em aplicativos de n camadas | Microsoft Docs"
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
  - "TableAdapters, aplicativos de n camadas"
  - "aplicativos de n camadas, estendendo o recurso TableAdapters"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Adicionar c&#243;digo a TableAdapters em aplicativos de n camadas
Você pode estender a funcionalidade de um `TableAdapter`,criando um arquivo classe parcial para a `TableAdapter` e Adicionando código a ele \(em vez de adicionar código para o  DatasetName. DataSet.Designer de arquivo\).  \(Classes parciais permitem codificar uma classe específica para ser dividida entre arquivos físicos múltiplos.  Para obter mais informações, consulte [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partial \(tipo\)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
 O código que define um `TableAdapter` é gerado sempre que forem feitas alterações de `TableAdapter` \(na caixa [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)\).  Esse código também é gerado quando alterações são feitas durante a execução de qualquer assistente que modifica a configuração de `TableAdapter`.  Para evitar que seu código seja deletado durante a regeneração do `TableAdapter`, adicione código ao ao arquivo da classe parcial da `TableAdapter`.  
  
 By default, after you separate the dataset and `TableAdapter` code, the result is a discrete class file in each project.  O projeto original tem um arquivo chamado  DatasetName. Designer.vb \(ou  DatasetName. Designer.cs\) que contém o código `TableAdapter`.  O projeto designado na caixa  **Projeto DataSet**  propriedade tem um arquivo chamado  *DatasetName* . DataSet.Designer.vb \(ou  DatasetName. DataSet.Designer.cs\) que contém o código de dataset.  
  
> [!NOTE]
>  Quando você separar DataSets e `TableAdapter` s \(definindo o  **DataSet Project**  Propriedade\), classes parciais DataSet existentes no projeto não serão movidas automaticamente.  Classes parciais DataSet existente devem ser movidas manualmente para o projeto DataSet.  
  
> [!NOTE]
>  O [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md) também fornece funcionalidade para gerar <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> manipuladores de eventos quando código de validação deve ser adicionado.  Para obter mais informações, consulte [Adicionar validação a um conjunto de dados de n camadas](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para adicionar o código do usuário a um TableAdapter em um aplicativo n\-camada  
  
1.  Localize o projeto que contém o arquivo .xsd \([Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Clique duas vezes no arquivo **.xsd** para abrir o [Criando e editando conjuntos de dados tipados](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Clique com o botão direito do mouse `TableAdapter` que você deseja adicionar código para e clique em  **Exibir código** .  
  
     Um classe parcial é criado e abre no Editor de Códigos.  
  
4.  Adicione um código de usuário dentro da declaração de classe parcial.  
  
5.  O exemplo a seguir mostra onde adicionar código para o `CustomersTableAdapter` na caixa `NorthwindDataSet`:  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## Consulte também  
 [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)   
 [Adicionar código ao datasets em aplicativos de n camadas](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [TableAdapters](../Topic/TableAdapters.md)   
 [Visão geral de TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Visão geral de atualização hierárquica](../Topic/Hierarchical%20Update%20Overview.md)   
 [Criando aplicativos de dados](../data-tools/creating-data-applications.md)