---
title: "IDiaStackFrame::get_lengthParams | Microsoft Docs"
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
  - "Método IDiaStackFrame::get_lengthParams"
ms.assetid: 78005efa-2883-4823-b4e4-711a66672c78
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_lengthParams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o número de bytes de parâmetros colocados no empilhamento.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o número de bytes de parâmetros.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se a propriedade não é suportada.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)