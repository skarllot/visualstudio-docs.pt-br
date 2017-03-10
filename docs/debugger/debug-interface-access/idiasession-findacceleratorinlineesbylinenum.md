---
title: "IDiaSession::findAcceleratorInlineesByLinenum | Microsoft Docs"
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
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findAcceleratorInlineesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retorna uma enumeração de símbolos de quadros internos que correspondem ao local especificado de origem.  
  
## Sintaxe  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parâmetros  
 `parent`  
 \[in\] `IDiaSymbol` que corresponde à função de stub de aceleradores que precisa ser pesquisada.  
  
 `file`  
 \[in\] `IDiaSourceFile` de local de origem.  
  
 `linenum`  
 \[in\] número da linha local de origem.  
  
 `colnum`  
 \[in\] número da coluna de local de origem.  
  
 `ppResult`  
 \[out\] um ponteiro à um ponteiro de interface de `IDiaEnumLineNumbers` que é inicializada com o resultado.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)