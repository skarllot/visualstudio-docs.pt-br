---
title: "Como depurar clientes e servidores COM usando a depura&#231;&#227;o RPC | Microsoft Docs"
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
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "clientes COM, depuração"
  - "servidores COM, depuração"
  - "COM, depuração"
  - "depuração de chamada de procedimento remoto no processo"
  - "depuração de chamada de procedimento remoto fora do processo"
  - "depuração remota, RPC (Chamada de Procedimento Remoto)"
  - "RPC (Chamada de Procedimento Remoto)"
  - "RPC (Chamada de Procedimento Remoto), depuração"
  - "RPC (Chamada de Procedimento Remoto), depurando clientes COM e servidores"
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como depurar clientes e servidores COM usando a depura&#231;&#227;o RPC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar a depuração de chamada de procedimento remoto \(RPC\) para depurar aplicativos cliente\/servidor COM.  Você deve habilitar a depuração de RPC para usá\-lo.  Com a depuração de RPC habilitada, quando você entrar na chamada do servidor do cliente, o depurador anexará ao servidor e permitirá depurar o código.  Quando o depurador for anexado, você poderá usar todos os recursos do depurador com o cliente e os processos do servidor.  
  
### Para habilitar a depuração de RPC  
  
1.  No menu **Ferramentas**, clique em **Opções**.  
  
2.  Na caixa de diálogo **Opções**, clique na pasta **Depuração**.  
  
3.  Clique na página **Nativo**.  
  
4.  Selecione a caixa de seleção **depuração de RPC**.  
  
    > [!NOTE]
    >  Para depurar chamadas de RPC, você deve ter privilégios de Administrador ou Usuário avançado.  
  
    > [!NOTE]
    >  A entrada de RPC em um servidor remoto que executa o Microsoft Windows Vista só funcionará se um depurador nativo for anexado ao servidor remoto.  Caso contrário, a chamada de RPC apresentará falha sem uma mensagem de erro.  De outro modo, a chamada de RPC será concluída, mas a depuração da chamada de RPC não funcionará.  
  
## Consulte também  
 [Depuração de servidor COM e contêiner](../debugger/com-server-and-container-debugging.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)