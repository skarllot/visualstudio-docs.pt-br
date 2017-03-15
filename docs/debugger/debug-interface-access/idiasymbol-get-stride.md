---
title: "IDiaSymbol::get_stride | Microsoft Docs"
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
ms.assetid: 4264742a-3d91-44b9-9d14-87adbc77f0f0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_stride
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o passo de matriz ou matriz strided.  
  
## Sintaxe  
  
```cpp  
HRESULT get_stride(   
   DWORD* pRetVal);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] um ponteiro da `DWORD` que contém o passo.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retornará `S_FALSE` ou um código de erro.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)