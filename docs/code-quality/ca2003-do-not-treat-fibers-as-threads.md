---
title: "CA2003: n&#227;o tratar fibras como threads | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
helpviewer_keywords: 
  - "CA2003"
  - "DoNotTreatFibersAsThreads"
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2003: n&#227;o tratar fibras como threads
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotTreatFibersAsThreads|  
|CheckId|CA2003|  
|Categoria|Microsoft.Reliability|  
|Alteração Significativa|Sem quebra|  
  
## Causa  
 Um thread gerenciado está sendo tratado como um thread Win32.  
  
## Descrição da Regra  
 Digamos que um thread gerenciado é um thread Win32.  É uma fibra.  Common Language Runtime \(CLR\) executará threads gerenciados como fibras no contexto de threads reais que são de propriedade do SQL.  Esses threads podem ser compartilhados pelos appdomains e até mesmo de bases de dados no processo do SQL Server.  Usar armazenamento de thread local gerenciado funcionará, mas você não pode usar o armazenamento de thread local não gerenciado ou presume que o código será executado no thread atual do sistema operacional novamente.  Não altere as configurações como a localidade do thread.  Não chame CreateCriticalSection ou CreateMutex por meio de P\/Invoke porque eles exigem que o thread que entra em um bloqueio também deve deixar o bloqueio.  Como esse não será o caso quando você usar fibras, as seções críticos e os mutexes do Win32 serão inúteis no SQL.  Você pode seguramente usar a maioria de estado em um objeto gerenciado de System.Thread.  Isso inclui o armazenamento de thread local gerenciado e a cultura atual de \(UI\) de interface de usuário do thread.  No entanto, por razões do modelo de programação, você não poderá alterar a cultura atual de um thread quando você usa SQL; isso será aplicada a uma nova permissão.  
  
## Como Corrigir Violações  
 Examine o uso de threads e altere seu código adequadamente.  
  
## Quando Suprimir Alertas  
 Você não deve omitir esta regra.