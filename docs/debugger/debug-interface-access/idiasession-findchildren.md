---
title: "IDiaSession::findChildren | Microsoft Docs"
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
  - "Método IDiaSession::findChildren"
ms.assetid: 5d19046f-f668-4aa9-8788-95cda9a98997
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findChildren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera todos os filhos de um identificador pai especificado corresponde ao tipo de nome e o símbolo.  
  
## Sintaxe  
  
```cpp#  
HRESULT findChildren (   
   IDiaSymbol*       parent,  
   SymTagEnum        symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parâmetros  
 `parent`  
 \[in\] Um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o pai do objeto.  Se esse símbolo pai é uma função, módulo ou bloco e seus filhos lexicais são retornados em `ppResult`.  Se o símbolo de pai é um tipo, seus filhos de classe são retornados.  Se este parâmetro for `NULL`, em seguida, `symtag` deve ser definido como `SymTagExe` ou `SymTagNull`, que retorna um escopo global \(arquivo. exe\).  
  
 `symtag`  
 \[in\] Especifica a marca de símbolo filhos a serem recuperados.  Valores são obtidas a partir do [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração.  Definido como `SymTagNull` para recuperar todos os filhos.  
  
 `name`  
 \[in\] Especifica o nome dos filhos devem ser recuperados.  Definido como `NULL` para todas as crianças a serem recuperados.  
  
 `compareFlags`  
 \[in\] Especifica as opções de comparação aplicadas a correspondência de nome.  Os valores da [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) enumeração pode ser usada isoladamente ou em conjunto.  
  
 `ppResult`  
 \[out\] Retorna um [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) recuperado do objeto que contém a lista de símbolos do filho.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Exemplo  
 O exemplo a seguir mostra como localizar variáveis locais da função `pFunc` esse nome de correspondência `szVarName`.  
  
```cpp#  
IDiaEnumSymbols* pEnum;  
pSession->findChildren( pFunc, SymTagData, szVarName, nsCaseSensitive, &pEnum );  
```  
  
## Consulte também  
 [Visão Geral](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)