---
title: "Ocorreu um erro de DCOM durante a tentativa de entrar em contato com o computador remoto. O acesso &#233; negado. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_access_denied"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "DCOM, erros de acesso"
  - "erro de acesso negado DCOM remoto"
  - "depuração remota, Erro DCOM"
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ocorreu um erro de DCOM durante a tentativa de entrar em contato com o computador remoto. O acesso &#233; negado.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Depuração remota usa DCOM para se comunicar entre os computadores locais e remotos nas situações a seguir:  
  
-   O depurador é definido como **modo de compatibilidade nativa** ou **modo de compatibilidade gerenciado** check\-in a **Ferramentas \/ opções \/ depuração** página  
  
-   Você está depurando C\+\+ gerenciado \(C \+ \+ \/ CLI\) código.  
  
-   No Visual Studio 2013, quando **Ativar nativo Edit and Continue** check\-in a **Ferramentas \/ opções \/ depuração** página  
  
-   Alguns cenários de depuração de terceiros  
  
 Esse erro ocorre quando o processo do Visual Studio não pode autenticar \(ou as credenciais fornecidas forem julgadas insuficientes\) para o processo do depurador remoto através de DCOM. Uma ou mais das seguintes alternativas podem resolver o problema:  
  
-   Desativar  **modo de compatibilidade nativa** e **modo de compatibilidade gerenciado**.  
  
-   No Visual Studio 2013, desative **Ativar nativo Edit and Continue**.  
  
-   Reinicialize ambos os computadores.  
  
-   Se a depuração remota exige a inserir credenciais, marque a opção para salvar as credenciais.  
  
## Consulte também  
 [Erros de depuração remota e solução de problemas](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Depuração remota](../debugger/remote-debugging.md)