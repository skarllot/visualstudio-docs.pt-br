---
title: "IDiaSymbol::findChildren | Microsoft Docs"
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
  - "Método IDiaSymbol::findChildren"
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera os filhos do símbolo.  
  
## Sintaxe  
  
```cpp#  
HRESULT findChildren (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parâmetros  
 `symtag`  
 \[in\] Especifica as marcas de símbolo filhos a serem recuperados, conforme definido na [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md).  Definido como `SymTagNull` para todas as crianças a serem recuperados.  
  
 `name`  
 \[in\] Especifica o nome dos filhos devem ser recuperados.  Definido como `NULL` para todas as crianças a serem recuperados.  
  
 `compareFlags`  
 \[in\] Especifica as opções de comparação aplicadas a correspondência de nome.  Os valores da [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada isoladamente ou em conjunto.  
  
 `ppResult`  
 \[out\] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) o objeto que contém uma lista dos símbolos filho recuperado.  
  
## Valor de retorno  
 Retorna `S_OK` se pelo menos um filho do símbolo foi encontrado ou retorna `S_FALSE` se sem filhos foram encontrados; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Este método é idêntico a chamar o [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md) método com esse símbolo, como o primeiro parâmetro.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)