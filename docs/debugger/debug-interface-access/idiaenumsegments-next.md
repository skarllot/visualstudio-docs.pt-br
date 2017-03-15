---
title: "IDiaEnumSegments::Next | Microsoft Docs"
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
  - "Método IDiaEnumSegments::Next"
ms.assetid: 53f61874-d821-47ab-a1f5-27e982804a6a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um número especificado de segmentos na seqüência de enumeração.  
  
## Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG         celt,   
   IDiaSegment** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
#### Parâmetros  
 celt  
 \[in\] O número de segmentos de enumerador a serem recuperados.  
  
 rgelt  
 \[out\] Uma matriz que deve ser preenchido com o desejado [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos que representam os segmentos.  
  
 pceltFetched  
 \[out\] Retorna o número de segmentos buscadas enumerador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não houver nenhum mais segmentos.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)