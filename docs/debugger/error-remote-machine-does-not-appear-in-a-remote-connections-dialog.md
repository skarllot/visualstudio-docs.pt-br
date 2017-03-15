---
title: "Erro: O computador remoto n&#227;o aparece em uma caixa de di&#225;logo conex&#245;es remotas | Microsoft Docs"
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
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: O computador remoto n&#227;o aparece em uma caixa de di&#225;logo conex&#245;es remotas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se o computador remoto não aparecer na caixa de diálogo conexões remotas, verifique as causas comuns.  
  
 Se você estiver usando o modo de compatibilidade gerenciado, verifique a documentação do Visual Studio 2010: [Solucionando problemas de depuração remota \- Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### Causas comuns desse erro  
  
-   O computador remoto está em execução em um computador que esteja em uma sub\-rede diferente. Para corrigir isso, digitar manualmente o nome do computador ou endereço IP na caixa de diálogo qualificador  
  
-   O depurador remoto não está em execução no computador remoto. Para corrigir esse problema, inicie o depurador remoto.  
  
-   O firewall está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir esse problema, configure o firewall para permitir que o Visual Studio e o depurador remoto \(msvsmon\) para se comunicar.  
  
-   Software antivírus está bloqueando a comunicação entre o Visual Studio e o computador remoto. Para corrigir esse problema, configure o software antivírus para permitir que o Visual Studio e o depurador remoto \(msvsmon\) para se comunicar.  
  
## Consulte também  
 [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)