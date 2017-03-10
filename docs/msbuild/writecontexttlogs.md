---
title: "WriteContextTLogs | Microsoft Docs"
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
  - "WriteContextTLogs"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "WriteContextTLogs"
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# WriteContextTLogs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Grava arquivos de logs para o contexto atual.  
  
## Sintaxe  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
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
 [WriteAllTLogs](../msbuild/writealltlogs.md)