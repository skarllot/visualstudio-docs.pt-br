---
title: "IDiaSymbol::getSrcLineOnTypeDefn | Microsoft Docs"
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
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::getSrcLineOnTypeDefn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o arquivo fonte e o número da linha que indica onde um tipo definido pelo usuário especificado está definido.  
  
## Sintaxe  
  
```cpp  
HRESULT getSrcLineOnTypeDefn(  
   IDiaLineNumber **ppResult);  
```  
  
#### Parâmetros  
 `ppResult`  
 \[out\] um objeto de `IDiaLineNumber` que contém o arquivo fonte e o número da linha onde o definido pelo usuário.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retornará `S_FALSE` ou um código de erro.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)