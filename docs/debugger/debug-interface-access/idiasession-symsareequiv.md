---
title: "IDiaSession::symsAreEquiv | Microsoft Docs"
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
  - "Método IDiaSession::symsAreEquiv"
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symsAreEquiv
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verifica se os dois símbolos são equivalentes.  
  
## Sintaxe  
  
```cpp#  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### Parâmetros  
 `symbolA`  
 \[in\] O primeiro [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto usado na comparação.  
  
 `symbolB`  
 \[in\] A segunda `IDiaSymbol` objeto usado na comparação.  
  
## Valor de retorno  
 Se os símbolos são equivalentes, retornará `S_OK`; Caso contrário, retornará `S_FALSE`, os símbolos não são equivalentes.  Caso contrário, retornará um código de erro.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)