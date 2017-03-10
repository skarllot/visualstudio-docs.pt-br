---
title: "Erro: depura&#231;&#227;o de modo misto para processos x64 s&#243; &#233; suportada durante o uso do Microsoft .NET Framework 4 ou superior | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erro: depura&#231;&#227;o de modo misto para processos x64 s&#243; &#233; suportada durante o uso do Microsoft .NET Framework 4 ou superior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Para depurar código nativo e gerenciado misto em um processo de 64 bits, você deverá ter a versão 4 do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  A depuração de modo misto de processos de 64 bits com as versões do [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] anteriores à 4 não tem suporte.  
  
### Para corrigir este erro  
  
-   Execute uma das seguintes etapas:  
  
    -   Atualize seu [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] para a versão 4.  
  
    -   Crie uma versão de 32 bits do aplicativo para depuração.  
  
## Consulte também  
 [Configurar as Ferramentas Remotas no dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)