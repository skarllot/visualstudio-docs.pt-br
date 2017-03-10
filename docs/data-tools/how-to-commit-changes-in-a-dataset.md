---
title: "Como confirmar altera&#231;&#245;es em um conjunto de dados | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DataSet.AcceptChanges"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "conjuntos de dados [Visual Basic], confirmando alterações"
ms.assetid: 51931353-4d22-4e35-a9ef-6f2b44e1f7d9
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Como confirmar altera&#231;&#245;es em um conjunto de dados
Quando você altera registros em um DataSet, atualizando, inserindo e excluindo registros, o dataset mantém versões originais e atuais dos registros.  Além disso, a propriedade <xref:System.Data.DataRow.RowState%2A> de cada linha rastreia se os registros estão em seu estado original ou se foram atualizados, inseridos ou excluídos.  Essas informações são úteis quando você precisa encontrar uma versão específica de uma linha.  Normalmente, você obteria um subconjunto de todos os registros alterados para enviar a outro processo.  Para obter mais informações, consulte [Como recuperar linhas alteradas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md).  Depois que tiver processado todas as linhas alteradas, você pode confirmar as alterações chamando o método `AcceptChanges` do <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow>.  O método `AcceptChanges` é chamado automaticamente ao chamar os métodos de atualização de uma [TableAdapter](../data-tools/tableadapter-overview.md) ou adaptador de dados.  Chame `AcceptChanges` após enviar alterações para um banco de dados.  
  
 Quando você chama <xref:System.Data.DataSet.AcceptChanges%2A> no <xref:System.Data.DataSet>, quaisquer objetos <xref:System.Data.DataRow> ainda em modo de edição terminam suas edições com êxito.  A propriedade <xref:System.Data.DataRow.RowState%2A> de cada <xref:System.Data.DataRow> também muda; linhas <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState> tornam\-se <xref:System.Data.DataRowState>, e linhas <xref:System.Data.DataRowState> são removidas.  
  
 Se o <xref:System.Data.DataSet> contiver objetos <xref:System.Data.ForeignKeyConstraint>, chamar o método <xref:System.Data.DataSet.AcceptChanges%2A> também faz com que o <xref:System.Data.AcceptRejectRule> seja aplicado.  
  
### Para confirmar alterações em um DataSet  
  
-   Chame o método `AcceptChanges` em um <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, ou <xref:System.Data.DataRow> para confirmar as alterações nesses objetos.  
  
     O exemplo a seguir mostra como chamar o método `AcceptChanges` para confirmar as alterações na tabela `Customers` após atualizar uma fonte de dados:  
  
     [!CODE [VbRaddataEditing#11](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataEditing#11)]  
  
## Consulte também  
 <xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>   
 <xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>   
 [Salvando dados](../data-tools/saving-data.md)   
 [Como recuperar linhas alteradas](../Topic/How%20to:%20Retrieve%20Changed%20Rows.md)