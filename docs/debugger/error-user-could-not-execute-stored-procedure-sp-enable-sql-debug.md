---
title: "Erro: o usu&#225;rio n&#227;o conseguiu executar o procedimento armazenado sp_enable_sql_debug | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.sqlde_accessdenied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: o usu&#225;rio n&#227;o conseguiu executar o procedimento armazenado sp_enable_sql_debug
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A depuração do Procedimento Armazenado sp\_enable\_sql\_debug não pode ser executada no servidor.  Isso pode ser causado por:  
  
-   Um problema de conexão.  Você precisa ter uma conexão estável com o servidor.  
  
-   Falta das permissões necessárias no servidor.  Para depurar no SQL Server 2005, a conta que executa o Visual Studio e a conta usada para conectar\-se ao SQL Server devem ser membros da função sysadmin.  A conta usada para se conectar ao SQL Server é sua conta de usuário do Windows \(se você estiver usando a autenticação do Windows\) ou uma conta com ID de usuário e senha \(se você usar a autenticação do SQL\).  
  
 Para obter mais informações, consulte [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/pt-br/84e088d0-0409-41d4-841b-f5d4b0fda414).  
  
## Consulte também  
 [How to: Set SQL Server Permissions for Debugging](http://msdn.microsoft.com/pt-br/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [Setting Up SQL Debugging](http://msdn.microsoft.com/pt-br/3db09e68-edcc-42de-9c22-4e97cfd55ab3)