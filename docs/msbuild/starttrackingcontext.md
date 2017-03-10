---
title: "StartTrackingContext | Microsoft Docs"
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
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inicie um contexto de rastreamento.  
  
## Sintaxe  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### Parâmetros  
 \[in\]`intermediateDirectory`  
 O diretório para armazenar o log de controle.  
  
 \[in\]`taskName`  
 Identifica o contexto de rastreamento.  Esse nome é usado para criar o nome do arquivo de log.  
  
## Valor de retorno  
 Um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) bit definido se o contexto de controle foi criado.  
  
## Requisitos  
 **Cabeçalho:** FileTracker.h