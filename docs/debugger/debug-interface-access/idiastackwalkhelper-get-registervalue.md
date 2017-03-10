---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
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
  - "Método IDiaStackWalkHelper2::get_registerValue"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::get_registerValue
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
 \[in\] Um valor a partir do [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md) especificando que se registrar para obter o valor de enumeração.  
  
 `pRetVal`  
 \[out\] Retorna o valor atual do registrador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Apesar do tamanho da `pRetVal` parâmetro, uma implementação deve armazenar apenas o que o registro normalmente contém.  Por exemplo, um registrador de 8 bits contém apenas o menor 8 bits de um determinado valor.  Esse valor de 8 bits é expandido para 64 bits quando retornado deste método.  
  
## Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeração CV\_HREG\_e](../../debugger/debug-interface-access/cv-hreg-e.md)