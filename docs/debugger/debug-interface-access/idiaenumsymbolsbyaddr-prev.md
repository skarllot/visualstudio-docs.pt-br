---
title: "IDiaEnumSymbolsByAddr::Prev | Microsoft Docs"
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
  - "Método IDiaEnumSymbolsByAddr::Prev"
ms.assetid: da3b3dca-68cb-4cb0-b25c-e28a1ffe49d3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::Prev
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera os símbolos anteriores na ordem por endereço.  
  
## Sintaxe  
  
```cpp#  
HRESULT Prev (   
   ULONG        celt,   
   IDiaSymbol** rgelt,  
   ULONG*       pceltFetched  
);  
```  
  
#### Parâmetros  
 celt  
 \[in\] O número de símbolos no enumerador a serem recuperados.  
  
 rgelt  
 \[out\] Uma matriz que deve ser preenchido com [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objetos que representam os símbolos desejados.  
  
 pceltFetched  
 \[out\] Retorna o número de símbolos buscadas enumerador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não houver nenhum símbolo anterior.  Caso contrário, retorna um código de erro.  
  
## Comentários  
 Esse método atualiza a posição do enumerador pelo número de elementos buscados.  
  
## Consulte também  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)