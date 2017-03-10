---
title: "Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.OracleClient.OracleException | Microsoft Docs"
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
  - "Classe OracleException"
  - "Oracle"
  - "exceções, Oracle"
ms.assetid: 08b9206e-baa9-4caa-b0c7-ece2118f6e2d
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Exce&#231;&#245;es de solu&#231;&#227;o de problemas: System.Data.OracleClient.OracleException
Um <xref:System.Data.OracleClient.OracleException> exceção é gerada quando um aviso ou erro é retornado por um banco de dados Oracle ou o provedor de dados .NET Framework para Oracle.  
  
## Dicas associadas  
 **Verifique se você está se conectando com credenciais válidas.**  
 Certifique\-se de que as credenciais que você está fornecendo são válidas.  
  
 **Verifique se o nome do servidor está correto e se o servidor está em execução.**  
 Verifique se você estiver usando o nome de servidor correto e que o servidor pode ser alcançado.  
  
## Comentários  
 Essa exceção é lançada sempre que o <xref:System.Data.OracleClient.OracleDataAdapter> encontra um erro gerado pelo servidor.  
  
 Se a gravidade do erro é muito grande, o servidor pode fechar o <xref:System.Data.OracleClient.OracleConnection>. No entanto, o usuário pode reabrir a conexão e continuar.  
  
## Consulte também  
 <xref:System.Data.OracleClient.OracleException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)