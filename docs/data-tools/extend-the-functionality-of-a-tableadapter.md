---
title: "Estender a funcionalidade de um TableAdapter | Microsoft Docs"
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
  - "dados [Visual Studio], TableAdapters"
  - "dados [Visual Studio], estendendo o recurso TableAdapters"
  - "TableAdapters, adicionando funcionalidade"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estender a funcionalidade de um TableAdapter
Você pode estender a funcionalidade de um TableAdapter adicionando código ao arquivo de classe parcial do TableAdapter.  
  
 O código que define um TableAdapter é regenerado quando alterações são feitas no TableAdapter \(no **Dataset Designer**\) ou quando alterações são feitas durante a execução de qualquer assistente que modifica a configuração de um TableAdapter. Para impedir que seu código seja excluído durante a regeneração de um TableAdapter, adicione código ao arquivo de classe parcial do TableAdapter.  
  
 \(Classes parciais permitem codificar uma classe específica ser dividida entre arquivos físicos múltiplos. Para obter mais informações, consulte [Parcial](/dotnet/visual-basic/language-reference/modifiers/partial) ou [partial \(tipo\)](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
## Localizando TableAdapters no código  
 Enquanto TableAdapters são criados com o **Dataset Designer**, as classes TableAdapter geradas não são geradas como classes aninhadas do <xref:System.Data.DataSet>. TableAdapters estão localizados em um namespace baseado no nome do dataset associado do TableAdapter. Por exemplo, se seu aplicativo contém um conjunto de dados chamado `HRDataSet`, o TableAdapters deve estar localizado no `HRDataSetTableAdapters` namespace. \(A convenção de nomeação segue este padrão: *DatasetName* \+ `TableAdapters`\).  
  
 O exemplo a seguir supõe um TableAdapter chamado `CustomersTableAdapter` em um projeto com um `NorthwindDataSet`.  
  
#### Para criar uma classe parcial para um TableAdapter  
  
1.  Adicione uma nova classe ao seu projeto, escolhendo **Add Class** do **projeto** menu.  
  
2.  Nomeie a classe `CustomersTableAdapterExtended`.  
  
3.  Clique em **Adicionar**.  
  
4.  Substitua o código com o namespace apropriado e o nome de classe parcial para seu projeto. Por exemplo:  
  
     [!CODE [VbRaddataTableAdapters#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#2)]  
  
## Consulte também  
 [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)