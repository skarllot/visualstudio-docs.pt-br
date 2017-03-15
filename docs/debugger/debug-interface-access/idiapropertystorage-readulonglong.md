---
title: "IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadULONGLONG"
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lê `ULONGLONG` valores em um conjunto de propriedades.  
  
## Sintaxe  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### Parâmetros  
 `id`  
 \[in\] Identificador da propriedade para ser lido \(`PROPID` é definido em WTypes.h como um `ULONG`\).  
  
 `pValue`  
 \[out\] Retorna o valor da propriedade.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  Retorna `E_INVALIDARG` se a propriedade não é do tipo `ULONGLONG`.  
  
## Comentários  
 A `ULONGLONG` é definido pelo Windows como um inteiro não assinado de 64 bits.  
  
## Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)