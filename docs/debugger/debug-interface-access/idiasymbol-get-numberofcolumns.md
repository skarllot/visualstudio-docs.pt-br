---
title: "IDiaSymbol::get_numberOfColumns | Microsoft Docs"
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
ms.assetid: 64834351-e2c9-4f1c-9dc0-2abb5478bc63
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_numberOfColumns
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o número de colunas da matriz.  
  
## Sintaxe  
  
```cpp  
HRESULT get_numberOfColumns(   
   DWORD* pRetVal);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Um ponteiro para um `DWORD` que contém o número de colunas da matriz.  
  
## Valor de retorno  
 Se for bem\-sucedido, retornará `S_OK`; caso contrário, retorna `S_FALSE` ou um código de erro.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)