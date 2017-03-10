---
title: "StopTrackingAndCleanup | Microsoft Docs"
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
  - "StopTrackingAndCleanup"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pára o rastreamento de todas as e libera as memórias usada pela sessão de rastreamento.  
  
## Sintaxe  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## Valor de retorno  
 Retorna um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) bit definido se o rastreamento foi interrompido.  
  
## Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)