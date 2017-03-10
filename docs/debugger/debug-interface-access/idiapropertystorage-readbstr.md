---
title: "IDiaPropertyStorage::ReadBSTR | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBSTR"
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lê `BSTR` valores em um conjunto de propriedades.  
  
## Sintaxe  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### Parâmetros  
 `id`  
 \[in\] Identificador da propriedade para ser lido \(`PROPID` é definido em WTypes.h como um `ULONG`\).  
  
 `pValue`  
 \[out\] Retorna o valor da propriedade.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  Retorna `E_INVALIDARG` se a propriedade não é do tipo `BSTR`.  
  
## Comentários  
 A `BSTR` é definido pelo Windows como uma seqüência de caracteres largos terminada em zero.  
  
## Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)