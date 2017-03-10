---
title: "EndTrackingContext | Microsoft Docs"
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
  - "EndTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "EndTrackingContext"
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# EndTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Finalize o contexto atual do controle.  
  
## Sintaxe  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## Valor de retorno  
 Um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) bit definido se o contexto de rastreamento foi finalizado.  
  
## Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)