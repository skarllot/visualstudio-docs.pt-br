---
title: "IDiaSession::findSymbolByAddr | Microsoft Docs"
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
  - "Método IDiaSession::findSymbolByAddr"
ms.assetid: c130abc5-4d0a-4d2d-8286-94fde36ddd4a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findSymbolByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um tipo de símbolo especificado que contém ou é mais próximo a um endereço especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT findSymbolByAddr (   
   DWORD        isect,  
   DWORD        offset,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Parâmetros  
 `isect`  
 \[in\] Especifica o componente de seção do endereço.  
  
 `offset`  
 \[in\] Especifica o componente de compensação do endereço.  
  
 `symtag`  
 \[in\] Tipo de símbolo a ser localizado.  Valores são obtidas a partir do [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração.  
  
 `ppSymbol`  
 \[out\] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperado do objeto que representa o símbolo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Exemplo  
  
```cpp#  
IDiaSymbol* pFunc;  
pSession->findSymbolByAddr( isect, offset, SymTagFunction, &pFunc );  
```  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)