---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Define por sua presença se o arquivo de log de gráficos é salvo para o diretório de arquivos temporários do usuário.  
  
## Sintaxe  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## Valor  
 Um símbolo do pré\-processador que, por sua presença ou ausência determina se o arquivo de log de gráficos é salvo para o diretório de arquivos temporários do usuário. Se esse símbolo é definido, o nome de arquivo definido por `VSG_DEFAULT_RUN_FILENAME` é relativo ao diretório atual do aplicativo capturado ou é um caminho absoluto; caso contrário, o nome de arquivo definido por `VSG_DEFAULT_RUN_FILENAME` é relativo ao diretório de arquivos temporários do usuário e não pode ser um caminho absoluto.  
  
## Comentários  
 Dependendo dos privilégios do usuário, o arquivo de log de gráficos não poderá ser salvo em um local arbitrário. É recomendável que você preferir salvar os logs de gráficos no diretório de arquivos temporários do usuário ou de outro local válida, se você não tiver certeza se o local em que você escolheria pode ser gravado pelo usuário.  
  
 Para impedir que o arquivo de log de gráficos que está sendo salvo no diretório de arquivos temporários, você deve definido `DONT_SAVE_VSGLOG_TO_TEMP` antes de incluir `vsgcapture. h`.  
  
## Exemplo  
 Este exemplo mostra como salvar o arquivo de log de elementos gráficos em um caminho absoluto no computador host.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## Consulte também  
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)