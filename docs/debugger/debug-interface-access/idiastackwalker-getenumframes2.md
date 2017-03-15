---
title: "IDiaStackWalker::getEnumFrames2 | Microsoft Docs"
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
  - "Método IDiaStackWalker2::getEnumFrames2"
ms.assetid: 73196d3f-112c-4b3a-997b-7c6b815d4afc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalker::getEnumFrames2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um enumerador de quadro de pilha para um tipo de plataforma específica.  
  
## Sintaxe  
  
```cpp#  
  
      HRESULT getEnumFrames2(   
   enum  CV_CPU_TYPE_e    cpuid,  
   IDiaStackWalkHelper*   pHelper,  
   IDiaEnumStackFrames**  ppEnum  
);  
```  
  
#### Parâmetros  
 `cpuid`  
 \[in\] Um valor a partir do [Enumeração CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) enumeração, especificando o tipo de plataforma.  
  
 `pHelper`  
 \[in\] O auxiliar [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) objeto.  
  
 `ppEnum`  
 \[out\] Retorna um [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) objeto contendo uma lista de [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) objetos.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Para obter uma lista de quadro de pilha para apenas a plataforma x86, chame o [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) método.  
  
## Consulte também  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)   
 [Enumeração CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)