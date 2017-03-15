---
title: "Erro: n&#227;o foi poss&#237;vel se conectar &#224; m&#225;quina &lt;name&gt;. A m&#225;quina n&#227;o pode ser localizada na rede. | Microsoft Docs"
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
  - "vs.debug.remote.dcom_disabled"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DCOM, erro não é possível se conectar"
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: n&#227;o foi poss&#237;vel se conectar &#224; m&#225;quina &lt;name&gt;. A m&#225;quina n&#227;o pode ser localizada na rede.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse comportamento ocorre se uma das seguintes condições for verdadeira:  
  
-   Sua conexão com o computador remoto foi interrompida.  
  
-   Sua conta de usuário no computador remoto está desabilitada.  
  
-   Sua senha no computador remoto expirou.  
  
### Para resolver esse comportamento:  
  
-   Verifique se o computador local e o computador remoto estão na mesma rede.  Para fazer isso, use o Microsoft Windows Explorer \(ou Pesquisador de Arquivos\) para tentar acessar o computador remoto.  
  
     — e —  
  
-   Verifique se a conta de usuário que você está usando para se conectar ao computador remoto está habilitada.  
  
     — e —  
  
-   Verifique se a senha que você está usando para se conectar ao computador remoto está válida e não expirou.  
  
## Consulte também  
 [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Configurações de depuração e preparação](../debugger/debugger-settings-and-preparation.md)