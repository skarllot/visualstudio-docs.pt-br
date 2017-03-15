---
title: "IDiaEnumLineNumbers::Item | Microsoft Docs"
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
  - "Método IDiaEnumLineNumbers::Item"
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumLineNumbers::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um número de linha por meio de um índice.  
  
## Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### Parâmetros  
 índice  
 \[in\] Índice da [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) o objeto a ser recuperado.  O índice está em um intervalo de 0 a `count`\-1, onde `count` é retornado pelo [IDiaEnumLineNumbers::get\_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) método.  
  
 lineNumber  
 \[out\] Retorna um [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) objeto que representa o número de linha desejada.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)