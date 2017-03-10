---
title: "N&#227;o foi poss&#237;vel devolver informa&#231;&#245;es de recursos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_scan_failed"
ms.assetid: e4389ff0-eb64-4c31-b32f-5216c73fadfb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# N&#227;o foi poss&#237;vel devolver informa&#231;&#245;es de recursos
Verificando a hierarquia de arquivos. resx falhou.  
  
 Como parte do `Preparing resources` etapa de compilação, que é mostrada no **saída** janela, o sistema de projeto examina a hierarquia de projeto para todos os arquivos com uma extensão. resx. Esta ação irá gerar uma lista de arquivos. resx XML precisam ser transformadas em arquivos. Resources binários antes de poderem ser incluídos como recursos na saída do projeto.  
  
 **Para corrigir este erro**  
  
-   Reiniciar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se isso não funcionar, Atendimento Microsoft para relatar o problema.  
  
     Esse erro fará com que uma compilação falhar.  
  
## Consulte também  
 [Tipos de arquivo e extensões de arquivo no Visual Basic e Visual c\#](http://msdn.microsoft.com/pt-br/f793852c-da06-4d52-a826-65f635844772)