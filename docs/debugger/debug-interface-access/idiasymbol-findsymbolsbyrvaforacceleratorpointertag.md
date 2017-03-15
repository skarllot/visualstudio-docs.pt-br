---
title: "IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs"
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um determinado valor correspondente da marca, esse método retorna uma enumeração de símbolos que estão contidos em essa função de stub em um endereço virtual relativo especificado.  
  
## Sintaxe  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### Parâmetros  
 `tagValue`  
 \[in\] o valor da marca do ponteiro para o símbolo de pointee registra for encontrado.  
  
 `rva`  
 \[in\] rva o que é usado para filtrar os símbolos que correspondem à variável de pointee com o valor especificado da marca.  
  
 `ppResult`  
 \[out\] um ponteiro à um ponteiro de interface de `IDiaEnumSymbols` que é inicializada com o resultado.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retornará `S_FALSE` ou um código de erro.  
  
## Comentários  
 Chamar este método somente em uma interface de `IDiaSymbol` que corresponde a uma função de stub de aceleração.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)