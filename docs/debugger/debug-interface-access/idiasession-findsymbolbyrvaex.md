---
title: "IDiaSession::findSymbolByRVAEx | Microsoft Docs"
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
  - "Método IDiaSession::findSymbolByRVAEx"
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolByRVAEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um tipo de símbolo especificado que contém ou está mais próximo de um endereço virtual relativo especificado \(RVA\) e o deslocamento.  
  
## Sintaxe  
  
```cpp#  
HRESULT findSymbolByRVAEx (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### Parâmetros  
 `rva`  
 \[in\] Especifica o RVA.  
  
 `symtag`  
 \[in\] Tipo de símbolo a ser localizado.  Valores são obtidas a partir do [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração.  
  
 `ppSymbol`  
 \[out\] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperado do objeto que representa o símbolo.  
  
 `displacement`  
 \[out\] Retorna um valor especificando um deslocamento do endereço virtual relativo especificado em `rva`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Exemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );  
```  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)