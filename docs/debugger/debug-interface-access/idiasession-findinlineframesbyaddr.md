---
title: "IDiaSession::findInlineFramesByAddr | Microsoft Docs"
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
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma enumeração que permite que um cliente executa iterações através dos quadros definidas em um endereço especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   IDiaSymbol*       parent,  
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parâmetros  
 `parent`  
 \[in\] um objeto de `IDiaSymbol` que representa o pai.  
  
 `isect`  
 \[in\] especifica o componente da seção de endereços.  
  
 `offset`  
 \[in\] especifica o deslocamento de endereços.  
  
 `ppResult`  
 \[out\] contém um objeto de `IDiaEnumSymbols` que contém a lista de quadros que são recuperados.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)