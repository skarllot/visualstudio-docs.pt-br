---
title: "ResumeTracking | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Currículos de controle no contexto atual.  
  
## Sintaxe  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## Valor de retorno  
 Um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) bit definido se o rastreamento foi retomado.  [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True)será retornado se o controle não é possível continuar porque o contexto não estava disponível.  
  
## Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## Consulte também  
 [SuspendTracking](../msbuild/suspendtracking.md)