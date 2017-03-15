---
title: "IDiaSegment::get_virtualAddress | Microsoft Docs"
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
  - "Método IDiaSegment::get_virtualAddress"
ms.assetid: 30073dd0-c864-4c4a-8863-80f243419f6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment::get_virtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o endereço virtual \(VA\) do início da seção.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_virtualAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o VA de início da seção.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há suporte para esta propriedade.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)