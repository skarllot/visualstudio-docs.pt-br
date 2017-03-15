---
title: "IDiaEnumLineNumbers::Next | Microsoft Docs"
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
  - "Método IDiaEnumLineNumbers::Next"
ms.assetid: 363d5b40-1316-4ab8-836f-63637f619e0a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumLineNumbers::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um número especificado de números de linha na seqüência de enumeração.  
  
## Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaLineNumber** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### Parâmetros  
 celt  
 \[in\] O número de números de linha o enumerador para serem recuperadas.  
  
 rgelt  
 \[out\] Retorna uma matriz de [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) objetos que representam os números de linha desejada.  
  
 pceltFetched  
 \[out\] Retorna o número de números de linhas buscadas enumerador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não houver nenhum mais números de linha.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)