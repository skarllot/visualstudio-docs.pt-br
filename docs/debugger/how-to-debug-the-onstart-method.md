---
title: "Como depurar o m&#233;todo OnStart | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
helpviewer_keywords: 
  - "Método OnStart"
  - "depuração [Visual Studio], serviços do Windows"
  - "depuração de código gerenciado, método OnStart"
  - "depuração de aplicativos de serviços do Windows, o método OnStart"
  - "Aplicativos de serviço do Windows, depuração"
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar o m&#233;todo OnStart
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode depurar um serviço do Windows ao iniciar o serviço e anexando o depurador ao processo do serviço. Para obter mais informações, consulte [How to: Debug Windows Service Applications](../Topic/How%20to:%20Debug%20Windows%20Service%20Applications.md). No entanto, para depurar o <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> método de um serviço do Windows, você deve iniciar o depurador de dentro do método.  
  
1.  Adicione uma chamada para <xref:System.Diagnostics.Debugger.Launch%2A> no início de `OnStart()`método.  
  
    ```c#  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Iniciar o serviço \(você pode usar `net start`, ou iniciá\-lo no **serviços** janela\).  
  
     Você verá uma caixa de diálogo semelhante à seguinte:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Selecione **Sim, depurar \< nome do serviço \>.**  
  
4.  Na janela do depurador Just\-In\-Time, selecione a versão do Visual Studio que você deseja usar para depuração.  
  
     ![JustInTimeDebugger](~/docs/debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Uma nova instância do Visual Studio é iniciado e a execução é interrompida no `Debugger.Launch()` método.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código gerenciado](../debugger/debugging-managed-code.md)