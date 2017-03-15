---
title: "Caixa de di&#225;logo Parar Depura&#231;&#227;o em Andamento | Microsoft Docs"
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
  - "vs.debug.stopnow"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Caixa de diálogo Parar Depuração em Andamento"
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Parar Depura&#231;&#227;o em Andamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Essa caixa de diálogo aparece quando o depurador está tentando interromper uma sessão de depuração, mas parar a sessão deve demorar um pouco.  Parar uma sessão de depuração normalmente é muito rápido e essa caixa de diálogo não é exibida.  Entretanto, às vezes, leva mais tempo para desanexar de todos os processos que estão sendo depurados.  Se parar a sessão levar mais do que alguns segundos \(ou se ocorrer um erro de desanexação\), essa caixa de diálogo será exibida.  Se isso ocorrer com frequência, poderá ser devido a um problema interno e você deverá entrar em contato com o Product Support Services.  
  
 Você pode esperar os processos desanexarem e essa caixa de diálogo desaparecer ou usar o botão **Parar Agora** para forçar a terminação imediata.  
  
 **Parar Agora**  
 Clique neste botão para encerrar imediatamente a sessão de depuração.  Usar **Parar Agora** encerrará em vez de desanexar os processos que estão sendo depurados.  Se você estiver depurando processos do sistema, encerrar os processos com **Parar Agora** poderá ter efeitos inesperados e indesejados.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Detaching Programs](http://msdn.microsoft.com/pt-br/f2c756c2-8079-474b-94c2-01c19a141a01)