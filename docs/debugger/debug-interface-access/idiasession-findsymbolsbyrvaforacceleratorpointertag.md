---
title: "IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um determinado valor correspondente da marca, esse método retorna uma enumeração de símbolos que estão contidos em um pai função especificada de stub de aceleradores em um endereço virtual relativo especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parâmetros  
 `parent`  
 \[in\] `IDiaSymbol` que corresponde à função de stub de aceleradores a ser pesquisada.  
  
 `tagValue`  
 \[in\] o valor da marca do ponteiro.  
  
 `rva`  
 \[in\] o endereço virtual relativo.  
  
 `ppResult`  
 \[out\] um ponteiro à um ponteiro de interface de `IDiaEnumSymbols` que é inicializada com o resultado.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Comentários  
 Chamar este método somente em uma interface de `IDiaSymbol` que corresponde a uma função de stub de aceleração.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)