---
title: "IDiaSegment::get_length | Microsoft Docs"
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
  - "Método IDiaSegment::get_length"
ms.assetid: 5d92e394-649b-49f2-bce7-12dd9d666d85
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment::get_length
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o número de bytes no segmento.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_ length (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o número de bytes no segmento.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há suporte para esta propriedade.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)