---
title: "IDiaPropertyStorage::ReadBOOL | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBOOL"
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lê `BOOL` valores em um conjunto de propriedades.  
  
## Sintaxe  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### Parâmetros  
 `id`  
 \[in\] Identificador da propriedade para ser lido \(`PROPID` é definido em WTypes.h como um `ULONG`\).  
  
 `pValue`  
 \[out\] Retorna o valor da propriedade.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  Retorna `E_INVALIDARG` se a propriedade não é do tipo `BOOL`.  
  
## Comentários  
 Para obter resultados consistentes, interpretar a `BOOL` valor para que sejam de valores diferentes de zero `TRUE` e zero é `FALSE`.  
  
## Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)