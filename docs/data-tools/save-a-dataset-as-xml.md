---
title: "Como salvar um conjunto de dados como XML | Microsoft Docs"
ms.custom: ""
ms.date: "10/06/2016"
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
  - "dados [Visual Studio], salvando como XML"
  - "conjuntos de dados [Visual Basic], salvando como XML"
  - "salvando dados"
  - "XML [Visual Basic], conjuntos de dados"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como salvar um conjunto de dados como XML
Os dados XML em um conjunto de dados podem ser acessados chamando os métodos XML disponíveis no conjunto de dados. Para salvar os dados em formato XML, você pode chamar o <xref:System.Data.DataSet.GetXml%2A> método ou o <xref:System.Data.DataSet.WriteXml%2A> método de um <xref:System.Data.DataSet>.  
  
 Chamar o <xref:System.Data.DataSet.GetXml%2A> método retorna uma cadeia de caracteres que contém os dados de todas as tabelas de dados no dataset formatado como XML.  
  
 Chamar o <xref:System.Data.DataSet.WriteXml%2A> método envia os dados formatados em XML para um arquivo que você especificar.  
  
### Para salvar os dados em um dataset como XML para uma variável  
  
-   O <xref:System.Data.DataSet.GetXml%2A> método retorna um <xref:System.String>, portanto, declare uma variável do tipo <xref:System.String> e atribua a ela os resultados do <xref:System.Data.DataSet.GetXml%2A> método.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### Para salvar os dados em um dataset como XML para um arquivo  
  
-   O <xref:System.Data.DataSet.WriteXml%2A> método tem várias sobrecargas. O código a seguir mostra como salvar os dados em um arquivo, então declare uma variável e atribua um caminho válido para salvar o arquivo.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)