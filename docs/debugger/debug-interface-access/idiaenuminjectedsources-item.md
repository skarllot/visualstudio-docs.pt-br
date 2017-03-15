---
title: "IDiaEnumInjectedSources::Item | Microsoft Docs"
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
  - "Método IDiaEnumInjectedSources::Item"
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumInjectedSources::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma fonte injetada por meio de um índice.  
  
## Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### Parâmetros  
 índice  
 \[in\] Índice da [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) o objeto a ser recuperado.  O índice é o intervalo de 0 a `count`\-1, onde `count` é retornado pelo [IDiaEnumInjectedSources::get\_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md) método.  
  
 injectedSource  
 \[out\] Retorna um [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objeto que representa a fonte injetada.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)