---
title: "IDiaEnumTables::Item | Microsoft Docs"
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
  - "Método IDiaEnumTables::Item"
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma tabela por meio de um índice ou nome.  
  
## Sintaxe  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### Parâmetros  
 `index`  
 \[in\] Índice ou nome da [IDiaTable](../../debugger/debug-interface-access/idiatable.md) a serem recuperados.  Se for usada uma variante integer, ele deve estar no intervalo de 0 a `count`\-1, onde `count` é conforme retornado pela [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) método.  
  
 `table`  
 \[out\] Retorna um [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto que representa a tabela desejada.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Se uma variante de seqüência de caracteres for especificada, a seqüência de caracteres nomeia uma determinada tabela.  O nome deve ser um dos nomes de tabela conforme definido na [Constantes \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## Exemplo  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## Consulte também  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Constantes \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)