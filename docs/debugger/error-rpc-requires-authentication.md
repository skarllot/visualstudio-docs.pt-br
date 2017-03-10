---
title: "Erro: RPC requer autentica&#231;&#227;o | Microsoft Docs"
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
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: RPC requer autentica&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O depurador do Visual Studio não pode se conectar ao computador remoto.  Uma política RPC está habilitada no computador local, impedindo a depuração remota.  
  
### Para corrigir este erro  
  
1.  Execute `\`*windir*`\system32\regedt32.exe`  
  
2.  Localize e exclua `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Reinicie o computador para que a alteração do Registro entre em vigor.  
  
4.  Se o problema persistir, contate o administrador de domínio sobre Configuração do Computador\-\>Modelos Administrativos\-\>Sistema\-\>Chamada de Procedimento Remoto\-\>Restrições para configuração de política de grupo de clientes RPC não autenticados.