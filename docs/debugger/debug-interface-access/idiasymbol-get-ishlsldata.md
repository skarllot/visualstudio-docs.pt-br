---
title: "IDiaSymbol::get_isHLSLData | Microsoft Docs"
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
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isHLSLData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica se esse símbolo representa dados de alto nível language \(HLSL\) de Características.  
  
## Sintaxe  
  
```cpp  
HRESULT get_isHLSLData(   
   BOOL* pRetVal);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] um ponteiro da `BOOL` que especifica se esse símbolo representa dados de HLSL.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retornará `S_FALSE` ou um código de erro.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)