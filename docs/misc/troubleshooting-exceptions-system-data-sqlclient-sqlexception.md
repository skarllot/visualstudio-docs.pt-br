---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.SqlClient.SqlException | Microsoft Docs"
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
  - "Classe SqlException"
ms.assetid: 05f63457-3825-4541-ae09-0c771eb5ba35
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.SqlClient.SqlException
Um <xref:System.Data.SqlClient.SqlException> exceção é gerada quando um aviso ou erro é retornado pelo SQL Server.  
  
## Dicas associadas  
 **Verifique se você está se conectando com credenciais válidas.**  
 Certifique\-se de que as credenciais que você está fornecendo são válidas. Para obter mais informações, consulte [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md).  
  
 **Verifique se o nome do servidor está correto e se o servidor está em execução.**  
 Verifique se você estiver usando o nome de servidor correto e que o servidor pode ser alcançado.  
  
### Comentários  
 Essa exceção é lançada sempre que o .NET Framework Data Provider para SQL Server encontra um erro gerado pelo servidor.  
  
 Mensagens com uma severidade de nível de 10 ou menos são informativas e indicam problemas causados por erros nas informações que um usuário inseriu. Níveis de severidade de 11 a 16 são gerados pelo usuário e podem ser corrigidos pelo usuário. Níveis de severidade de 17 a 25 indicam erros de software ou hardware. Quando um nível 17, 18 ou 19 erro ocorrer, você pode continuar trabalhando, embora você não poderá executar uma instrução específica.  
  
 O <xref:System.Data.SqlClient.SqlConnection> permanece aberto quando o nível de severidade é 19 ou menos. Quando o nível de severidade é 20 ou maior, o servidor geralmente encerra o <xref:System.Data.SqlClient.SqlConnection>. No entanto, o usuário pode reabrir a conexão e continuar. Em ambos os casos, um <xref:System.Data.SqlClient.SqlException> é gerado pelo método de execução do comando.  
  
 Para obter informações sobre as mensagens de aviso e informativas enviadas pelo SQL Server, consulte a seção de solução de problemas dos Manuais Online do SQL Server.  
  
## Consulte também  
 <xref:System.Data.SqlClient.SqlException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Access SQL Server Using Predetermined Credentials](../Topic/How%20to:%20Access%20SQL%20Server%20Using%20Predetermined%20Credentials.md)