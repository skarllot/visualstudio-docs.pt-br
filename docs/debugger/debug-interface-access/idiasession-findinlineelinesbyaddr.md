---
title: "IDiaSession::findInlineeLinesByAddr | Microsoft Docs"
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
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções que inlined, direta ou indiretamente, pelo símbolo pai especificado e está contida dentro do intervalo de endereços especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,  
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parâmetros  
 `parent`  
 \[in\] um objeto de `IDiaSymbol` que representa o pai.  
  
 `isect`  
 \[in\] especifica o componente da seção de endereços.  
  
 `offset`  
 \[in\] especifica o deslocamento de endereços.  
  
 `length`  
 \[in\] especificar o intervalo de endereços, em número de bytes, para cobrir com esta consulta.  
  
 `ppResult`  
 \[out\] contém um objeto de `IDiaEnumLineNumbers` que contém a lista de linha números que é recuperado.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)