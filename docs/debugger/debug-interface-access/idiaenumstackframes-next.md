---
title: "IDiaEnumStackFrames::Next | Microsoft Docs"
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
  - "Método IDiaEnumStackFrames::Next"
ms.assetid: 09378a21-d5e3-4213-b7e2-10f04d85295f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumStackFrames::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um número especificado de elementos do quadro de pilha na seqüência de enumeração.  
  
## Sintaxe  
  
```cpp#  
HRESULT Next(   
   ULONG             celt,  
   IDiaStackFrame**  rgelt,  
   ULONG*            pceltFetched  
);  
```  
  
#### Parâmetros  
 celt  
 \[in\] O número de elementos de stackframe enumerador a serem recuperados.  
  
 rgelt  
 \[out\] Uma matriz que deve ser preenchido com o solicitado [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objetos.  
  
 pceltFetched  
 \[out\] Retorna o número da pilha de elementos frame buscadas enumerador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não houver nenhum mais quadros de pilha.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)