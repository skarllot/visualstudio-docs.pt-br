---
title: "IDiaStackWalkFrame::get_registerValue | Microsoft Docs"
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
  - "Método IDiaStackWalkFrame::get_registerValue"
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o valor de um registrador.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### Parâmetros  
 `index`  
 \[in\] Um valor a partir do [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) especificando o registro para obter o valor de enumeração.  
  
 `pRetVal`  
 \[out\] Retorna o valor atual do registrador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)