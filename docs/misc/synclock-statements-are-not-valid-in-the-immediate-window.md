---
title: "Instru&#231;&#245;es &#39;SyncLock&#39; n&#227;o s&#227;o v&#225;lidas na janela imediata | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30135"
  - "bc30135"
helpviewer_keywords: 
  - "BC30135"
ms.assetid: 099771a1-5bf4-4c16-8fc3-262926c771df
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es &#39;SyncLock&#39; n&#227;o s&#227;o v&#225;lidas na janela imediata
O `SyncLock` instrução sincroniza segmentos e não é permitida em um contexto de depuração.  
  
 **ID do erro:** BC30135  
  
### Para corrigir este erro  
  
-   Não emita uma `SyncLock` instrução o **imediato** janela.  
  
## Consulte também  
 [Janela Imediata](../ide/reference/immediate-window.md)   
 [Instrução SyncLock](/dotnet/visual-basic/language-reference/statements/synclock-statement)