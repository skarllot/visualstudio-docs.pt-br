---
title: "Acessar diretamente o banco de dados com um TableAdapter | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "bancos de dados [Visual Basic], acessando com um TableAdapter"
  - "Métodos DBDirect"
  - "conjuntos de dados [Visual Basic], adicionando a projetos"
  - "salvamento de dados [Visual Studio]"
  - "Método TableAdapter.Delete"
  - "Propriedade GenerateDbDirectMethods"
  - "Método TableAdapter.Insert"
  - "Propriedade TableAdapter.GenerateDBDirectMethods"
  - "Método TableAdapter.Update"
  - "salvando dados"
  - "TableAdapters"
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Acessar diretamente o banco de dados com um TableAdapter
Além de `InsertCommand`, `UpdateCommand`, e `DeleteCommand`, TableAdapters são criados com métodos que podem ser executados diretamente no banco de dados. Esses métodos \(`TableAdapter.Insert`, `TableAdapter.Update`, e `TableAdapter.Delete`\) podem ser chamados diretamente para manipular dados no banco de dados.  
  
 Se você não deseja criar esses métodos diretos, defina o TableAdapter `GenerateDbDirectMethods` propriedade `false` no **propriedades** janela. Qualquer consulta adicionada a um TableAdapter além da consulta principal do TableAdapter é consultas autônomas — elas não geram esses métodos DbDirect.  
  
## Enviando comandos diretamente para um banco de dados  
 Chame o método TableAdapter DbDirect que executa a tarefa que você está tentando realizar.  
  
#### Para inserir novos registros diretamente em um banco de dados  
  
-   Chamar o TableAdapter `Insert` método, passando os valores para cada coluna como parâmetros. O procedimento a seguir usa o banco de dados Northwind `Region` tabela como um exemplo.  
  
    > [!NOTE]
    >  Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.  
  
     [!code-vb[VbRaddataSaving#15](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_1.vb)]
     [!code-cs[VbRaddataSaving#15](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_1.cs)]  
  
#### Para atualizar registros diretamente em um banco de dados  
  
-   Chamar o TableAdapter `Update` método, passando os valores novos e originais para cada coluna como parâmetros.  
  
    > [!NOTE]
    >  Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.  
  
     [!code-vb[VbRaddataSaving#18](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_2.vb)]
     [!code-cs[VbRaddataSaving#18](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_2.cs)]  
  
#### Para excluir registros diretamente de um banco de dados  
  
-   Chamar o TableAdapter `Delete` passando os valores para cada coluna como parâmetros do método de `Delete` método. \(Este exemplo usa o Northwind `Region` tabela.\)  
  
    > [!NOTE]
    >  Se você não tiver uma instância disponível, crie uma instância do TableAdapter que você deseja usar.  
  
     [!code-vb[VbRaddataSaving#21](../data-tools/codesnippet/VisualBasic/directly-access-the-database-with-a-tableadapter_3.vb)]
     [!code-cs[VbRaddataSaving#21](../data-tools/codesnippet/CSharp/directly-access-the-database-with-a-tableadapter_3.cs)]  
  
## Consulte também  
 [Preencher datasets usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)