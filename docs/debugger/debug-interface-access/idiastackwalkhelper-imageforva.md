---
title: "IDiaStackWalkHelper::imageForVA | Microsoft Docs"
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
  - "Método IDiaStackWalkHelper::imageForVA"
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::imageForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retorna o início da imagem de um executável memória recebe um endereço virtual em algum lugar no espaço de memória do executável.  
  
## Sintaxe  
  
```cpp#  
HRESULT imageForVA(  
   ULONGLONG  vaContext,  
   ULONGLONG *pvaImageStart  
);  
```  
  
#### Parâmetros  
 `vaContext`  
 \[in\] O endereço virtual que se encontra em algum lugar no espaço do executável.  
  
 `pvaImageStart`  
 \[out\] Retorna o endereço virtual inicial da imagem do executável.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)