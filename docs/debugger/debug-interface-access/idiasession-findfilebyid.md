---
title: "IDiaSession::findFileById | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Método IDiaSession::findFileById"
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um arquivo de origem pelo identificador de arquivo de origem.  
  
## Sintaxe  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### Parâmetros  
 `uniqueId`  
 \[in\] Especifica o identificador de arquivo de origem.  
  
 `ppResult`  
 \[out\] Retorna um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) recuperado do objeto que representa o arquivo de origem.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 O identificador de arquivo de origem é um valor exclusivo usado internamente para o SDK DIA para fazer com que todos os arquivos de origem exclusivo.  Este método geralmente é usado internamente para o SDK do DIA.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)