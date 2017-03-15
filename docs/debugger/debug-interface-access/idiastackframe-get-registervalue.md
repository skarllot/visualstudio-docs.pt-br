---
title: "IDiaStackFrame::get_registerValue | Microsoft Docs"
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
  - "Método IDiaStackFrame::get_registerValue"
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o valor de um registrador especificado conforme armazenado no quadro de pilha.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### Parâmetros  
 `registerIndex`  
 \[in\] Dentre as [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) valores de enumeração.  
  
 `pRetVal`  
 \[out\] Valor armazenado no registrador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna código de erro.  
  
## Consulte também  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)