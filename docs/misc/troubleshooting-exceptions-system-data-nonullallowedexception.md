---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.NoNullAllowedException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Classe NoNullAllowedException"
ms.assetid: 1ab87572-007f-4b84-bb13-c3626e7f89cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.NoNullAllowedException
Um <xref:System.Data.NoNullAllowedException> exceção é lançada quando há uma tentativa de inserir um valor nulo em uma coluna onde <xref:System.Data.DataColumn.AllowDBNull%2A> é definido como `false`.  
  
## Dicas associadas  
 **Verifique se o valor é DBNull antes de adicioná\-lo à coluna.**  
 Se <xref:System.Data.DataColumn.AllowDBNull%2A> for definido como `false`, você não poderá inserir um valor nulo. Para obter mais informações, consulte <xref:System.DBNull>.  
  
 **Defina AllowDBNull como true.**  
 Definir essa propriedade como `true` permitirá que você insira valores nulos. Para obter mais informações, consulte <xref:System.Data.DataColumn.AllowDBNull%2A>.  
  
## Comentários  
 Se você usar os botões de navegação para percorrer os registros de uma tabela de banco de dados em um formulário de dados, essa exceção pode ser lançada com as informações adicionais, "Column 'Column' não permite nulos." Esse comportamento ocorre porque a chave primária ou a coluna "not NULL" da tabela de banco de dados não foi selecionada no Assistente de formulário de dados. Se a chave primária ou a coluna "not NULL" do banco de dados não está selecionada no Assistente de formulário de dados quando você cria o formulário de dados, o **Add\-cria um novo registro** opção não está desabilitada. Para contornar esse problema, selecione as seguintes colunas da tabela selecionada quando você adicionar um formulário de dados usando o Assistente de formulário de dados: a coluna principal e uma coluna que não permita valores nulos.  
  
## Consulte também  
 <xref:System.Data.NoNullAllowedException>   
 <xref:System.Data.DataRowCollection.Add%2A>   
 <xref:System.Data.DataRow.EndEdit%2A>   
 <xref:System.Data.DataRow.ItemArray%2A>   
 <xref:System.Data.DataTable.LoadDataRow%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)