---
title: "Erro: firewall na m&#225;quina local | Microsoft Docs"
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
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: firewall na m&#225;quina local
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O firewall de conexão da Internet no computador local, o computador no qual você está executando o Visual Studio, não está configurado para permitir a depuração remota.  Para a depuração remota gerenciada ou nativa com o transporte padrão, a porta TCP 135 deve estar aberta para o tráfego de DCOM.  O compartilhamento de arquivos e impressoras deve ser aberto e o devenv.exe deve ser adicionado à lista de exceções.  Abrir algumas portas de IPSEC pode ser necessário também.  
  
 Para obter mais informações, consulte [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).