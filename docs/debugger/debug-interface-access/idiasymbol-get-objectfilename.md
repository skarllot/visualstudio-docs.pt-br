---
title: "IDiaSymbol::get_objectFileName | Microsoft Docs"
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
ms.assetid: 21793872-4879-4e4d-b527-dcf70aa7fb31
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_objectFileName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o nome de arquivo do objeto.  
  
## Sintaxe  
  
```cpp  
HRESULT get_objectFilename(   
   BSTR *pRetVal);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] um ponteiro da `BSTR` que contém o nome de arquivo do objeto.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retornará `S_FALSE` ou um código de erro.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)