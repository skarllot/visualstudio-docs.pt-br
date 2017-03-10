---
title: "Erro: o computador remoto n&#227;o conseguiu iniciar a comunica&#231;&#227;o DCOM | Microsoft Docs"
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
  - "vs.debug.error.unmarshal_callback_failed"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: o computador remoto n&#227;o conseguiu iniciar a comunica&#231;&#227;o DCOM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um erro DCOM ocorreu quando o computador remoto tentou se comunicar com o computador local.  O computador local é o computador que está  
  
 executando o Visual Studio.  Esse erro pode ocorrer por várias razões:  
  
-   O computador local tem um firewall habilitado.  
  
-   A autenticação do Windows do computador remoto para o computador local não está funcionando.  
  
### Para corrigir este erro  
  
1.  Se o computador local tiver o Firewall do Windows habilitado, consulte [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md) para obter instruções sobre como configurar o firewall para a depuração local.  
  
2.  Teste a autenticação do Windows tentando abrir um compartilhamento de arquivos no computador local do servidor remoto.  
  
3.  Para restaurar a autenticação do Windows, tente reiniciar os dois computadores.  Examine os logs de eventos nos computadores local e remoto para encontrar erros de Kerberos e entre em contato com os administradores de domínio para problemas conhecidos.  
  
## Consulte também  
 [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)