---
title: "StartTrackingContextWithRoot | Microsoft Docs"
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
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Inicia um contexto de rastreamento usando um arquivo de resposta especificando um marcador de raiz.  
  
## Sintaxe  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### Parâmetros  
 \[in\]`intermediateDirectory`  
 O diretório para armazenar o log de controle.  
  
 \[in\]`taskName`  
 Identifica o contexto de rastreamento.  Esse nome é usado para criar o nome do arquivo de log.  
  
 \[in\]`rootMarkerResponseFile`  
 O nome do caminho de um arquivo de resposta que contém um marcador de raiz.  O nome da raiz é usado para agrupar controlando todos os de um contexto juntos.  
  
## Valor de retorno  
 Um [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) com o [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True) bit definido se o contexto de controle foi criado.  
  
## Requisitos  
 **Cabeçalho:** FileTracker.h  
  
## Consulte também  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)