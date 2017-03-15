---
title: "IDiaEnumInjectedSources::Next | Microsoft Docs"
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
  - "Método IDiaEnumInjectedSources::Next"
ms.assetid: 38af80fc-748f-4b15-bff1-823db21dd4d0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumInjectedSources::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um número especificado de fontes injetados na seqüência de enumeração.  
  
## Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG                celt,   
   IDiaInjectedSource** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### Parâmetros  
 celt  
 \[in\] O número de fontes injetados enumerador a serem recuperados.  
  
 rgelt  
 \[out\] Retorna uma matriz de [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) objetos que representam as fontes injetadas desejadas.  
  
 pceltFetched  
 \[out\] Retorna o número de fontes injetados buscadas enumerador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se há fontes não mais injetados.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)