---
title: "Erro: o Monitor de Depura&#231;&#227;o Remota do Microsoft Visual Studio no computador remoto est&#225; sendo executado como um usu&#225;rio diferente | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "opção anyuser"
  - "opção -anyuser"
  - "msvsmon.exe"
  - "Monitor de Depuração Remota"
  - "depuração remota, Monitor de Depuração Remota"
ms.assetid: e5b18734-2daf-4c58-b5de-24ae1295703e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: o Monitor de Depura&#231;&#227;o Remota do Microsoft Visual Studio no computador remoto est&#225; sendo executado como um usu&#225;rio diferente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao tentar fazer a depuração remota, você pode receber a seguinte mensagem de erro:  
  
 O Monitor de Depuração Remota do Microsoft Visual Studio no computador está sendo executado como um usuário diferente.  
  
## Causa  
 Essa mensagem ocorre quando você está depurando no modo Sem Autenticação e o usuário que iniciou o msvsmon não é o usuário que está executando o Visual Studio.  
  
## Solução  
 A solução melhor e mais segura é executar o Monitor de Depuração Remota \(msvsmon.exe\) na mesma conta de usuário que o Visual Studio.  Se você não puder fazer isso, poderá executar o Monitor de Depuração Remota em outra conta com a opção **Permitir que qualquer usuário depure** selecionada na caixa de diálogo **Opções** do Monitor de Depuração Remota.  
  
> [!CAUTION]
>  Conceder permissões a outros usuários para se conectar permite a possibilidade de acidentalmente conectar à sessão de depuração remota incorreta.  A depuração no modo **Sem Autenticação** nunca é segura e deve ser usada com cuidado.  
  
 Para obter mais informações, consulte [Iniciar o Monitor de Depuração Remota](../Topic/Start%20%20the%20Remote%20Debugging%20Monitor.md).  
  
## Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)