---
title: "IDiaSymbol::get_thunkOrdinal | Microsoft Docs"
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
  - "Método IDiaSymbol::get_thunkOrdinal"
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o tipo de conversão de uma função.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um valor a partir do [Enumeração THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md) enumeração que especifica o tipo de conversão de uma função.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 Esta propriedade é válida somente se o símbolo como um [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valor de `SymTagThunk`.  
  
 Uma "conversão" é um trecho de código que converte entre um espaço de endereço de memória de 32 bits \(também conhecido como o espaço de endereço plano\) e um espaço de endereço de 16 bits \(conhecido como um espaço de endereçamento segmentado\).  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração THUNK\_ORDINAL](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)