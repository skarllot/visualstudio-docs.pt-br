---
title: "Como salvar dados usando uma transa&#231;&#227;o | Microsoft Docs"
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
  - "dados [Visual Studio], salvar"
  - "salvando dados, usando transações"
  - "Namespace System.Transactions"
  - "transações, salvando dados"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Como salvar dados usando uma transa&#231;&#227;o
Salvar dados em uma transação usando o <xref:System.Transactions> namespace. Use o <xref:System.Transactions.TransactionScope> objeto participe de uma transação que é gerenciada automaticamente para você.  
  
 Projetos não são criados com uma referência ao assembly System. Transactions, portanto você precisa adicionar manualmente uma referência aos projetos que usam transações.  
  
> [!NOTE]
>  O <xref:System.Transactions> namespace tem suporte no Windows 2000 e posterior.  
  
 A maneira mais fácil para implementar uma transação é instanciar um <xref:System.Transactions.TransactionScope> do objeto em um `using` instrução. \(Para obter mais informações, consulte [Instrução Using](/dotnet/visual-basic/language-reference/statements/using-statement), e [Instrução using](/dotnet/csharp/language-reference/keywords/using-statement).\) O código executado dentro do `using` instrução participará da transação.  
  
 Para confirmar a transação, chame o <xref:System.Transactions.TransactionScope.Complete%2A> bloquear o método como a última instrução em uso.  
  
 Para reverter a transação, lançar uma exceção antes de chamar o <xref:System.Transactions.TransactionScope.Complete%2A> método.  
  
 Para obter mais informações, consulte [Instruções passo a passo: salvando dados em uma transação](../data-tools/save-data-in-a-transaction.md).  
  
### Para adicionar uma referência para a dll System. Transactions  
  
1.  Do **projeto** menu, escolha **Adicionar referência**.  
  
2.  Selecione **System. Transactions** sobre o **.NET** guia \(**SQL Server** guia para projetos do SQL Server\) e clique em **OK**.  
  
     Uma referência para System.Transactions.dll é adicionada ao projeto.  
  
### Para salvar dados em uma transação  
  
-   Adicione código para salvar dados dentro do usando instrução que contém a transação. O código a seguir mostra como criar e instanciar um <xref:System.Transactions.TransactionScope> objeto no uso de uma instrução:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## Consulte também  
 [Salvar dados no banco de dados](../data-tools/save-data-back-to-the-database.md)