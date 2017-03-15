---
title: "IDiaSymbol::get_isSafeBuffers | Microsoft Docs"
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
  - "Método IDiaSymbol::get_isSafeBuffers"
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isSafeBuffers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um sinalizador que especifica se a diretiva de preprocesser para um buffer de seguro é usada.  Use quando o [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) for definido como `SymTagFunction`.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_isSafeBuffers(   
   BOOL* pRetVal)  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna `TRUE` se o ponteiro usa uma diretiva de pré\-processamento para um buffer de seguro; Caso contrário, retornará `FALSE`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [strict\_gs\_check](/visual-cpp/preprocessor/strict-gs-check)