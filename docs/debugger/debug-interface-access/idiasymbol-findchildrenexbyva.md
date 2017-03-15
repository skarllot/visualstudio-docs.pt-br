---
title: "IDiaSymbol::findChildrenExByVA | Microsoft Docs"
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
  - "IDiaSymbol::findChildrenExByVA"
ms.assetid: 29080009-36e4-4697-acd7-50f2e3e1bf1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findChildrenExByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera os filhos do símbolo que são válidos em um endereço virtual especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT findChildrenExByVA (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parâmetros  
 `symtag`  
 \[in\] Especifica as marcas de símbolo filhos a serem recuperados, conforme definido na [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md).  Definido como `SymTagNull` para todas as crianças a serem recuperados.  
  
 `name`  
 \[in\] Especifica o nome dos filhos devem ser recuperados.  Definido como `NULL` para todas as crianças a serem recuperados.  
  
 `compareFlags`  
 \[in\] Especifica as opções de comparação a ser aplicado a correspondência de nome.  Os valores da [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada isoladamente ou em conjunto.  
  
 `address`  
 \[in\] Especifica o endereço virtual.  
  
 `ppResult`  
 \[out\] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) o objeto que contém uma lista dos símbolos filho recuperado.  
  
## Valor de retorno  
 Retorna `S_OK` se pelo menos um filho do símbolo foi encontrado ou retorna `S_FALSE` se sem filhos foram encontrados; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Os símbolos locais que são retornados incluem informações sobre o intervalo ao vivo.  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)