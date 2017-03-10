---
title: "WriteAllTLogs | Microsoft Docs"
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
  - "WriteAllTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteAllTLogs"
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteAllTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grava os logs de rastreamento para todos os threads e contextos.  
  
## Sintaxe  
  
```  
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### Parâmetros  
 \[in\]`intermediateDirectory`  
 O diretório para armazenar o log de controle.  
  
 \[in\]`tlogRootName`  
 O nome da raiz do nome do arquivo de log.  
  
## Valor de retorno  
 Um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) bit definido se o contexto de controle foi criado.  
  
## Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## Consulte também  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)