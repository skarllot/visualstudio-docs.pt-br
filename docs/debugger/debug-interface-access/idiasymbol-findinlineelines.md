---
title: "IDiaSymbol::findInlineeLines | Microsoft Docs"
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
ms.assetid: 56ba4bc0-8f96-47c2-8b18-332b4e7c2d91
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findInlineeLines
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma enumeração que permite que um cliente executa iterações através da linha informações do número das funções que inlined, direta ou indiretamente, em esse símbolo.  
  
## Sintaxe  
  
```cpp#  
HRESULT findInlineeLines (   
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parâmetros  
 `ppResult`  
 \[out\] contém um objeto de `IDiaEnumLineNumbers` que contém a lista de linha números que é recuperado.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)