---
title: "IDiaSymbol::get_acceleratorPointerTags | Microsoft Docs"
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
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retorna todos os valores da marca do ponteiro de aceleradores que correspondem à função de stub de aceleração de AMP de C\+\+.  
  
## Sintaxe  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### Parâmetros  
 `cnt`  
 \[in\] o tamanho da matriz de saída `pPointerTags`.  
  
 `pcnt`  
 \[out\] o número de marcas ponteiro de aceleradores na função de stub de aceleração de AMP C\+\+.  
  
 `pPointerTags`  
 \[out\] o ponteiro de matriz de `DWORD` que é preenchido com a marca do ponteiro de aceleradores avalia na função de stub de aceleração de AMP C\+\+.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retornará `S_FALSE` ou um código de erro.  
  
## Comentários  
 Este método é chamado uma interface de `IDiaSymbol` que corresponde à função de stub de aceleração de AMP de C\+\+.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)