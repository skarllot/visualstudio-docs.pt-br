---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.StrongTypingException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe StrongTypingException"
ms.assetid: 90859ce2-3696-43cb-baf4-7daf98d8e2e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.StrongTypingException
A <xref:System.Data.StrongTypingException> ocorre quando o usuário acessa uma <xref:System.DBNull> valor fortemente tipado <xref:System.Data.DataTable.DataSet%2A>.  
  
## Dicas associadas  
 **Adicione tratamento de erro para o StrongTypingException.**  
 Coloque o código que acessa o <xref:System.Data.DataTable.DataSet%2A> em um `Try…Catch` Bloquear e capturar a <xref:System.Data.StrongTypingException>.  
  
## Consulte também  
 <xref:System.Data.DataTable.DataSet%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Instrução Try...Catch...Finally](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)   
 [Ferramentas do conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)