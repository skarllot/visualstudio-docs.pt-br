---
title: "IDiaSession::findInlineFramesByVA | Microsoft Docs"
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
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma enumeração que permite que um cliente executa iterações através dos quadros definidas em um endereço virtual especificado \(VA\).  
  
## Sintaxe  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,  
   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parâmetros  
 `parent`  
 \[in\] um objeto de `IDiaSymbol` que representa o pai.  
  
 `va`  
 \[in\] especifica o endereço como um VA.  
  
 `ppResult`  
 \[out\] contém um objeto de `IDiaEnumSymbols` que contém a lista de quadros que são recuperados.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)