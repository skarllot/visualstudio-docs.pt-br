---
title: "IDiaStackWalkHelper::symbolForVA | Microsoft Docs"
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
  - "Método IDiaStackWalkHelper::symbolForVA"
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::symbolForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o símbolo que contém o endereço virtual especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### Parâmetros  
 `va`  
 \[in\] O endereço virtual que está contido no símbolo solicitado.  O símbolo deve ser um `SymTagFunctionType` \(um valor a partir do [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração\).  
  
 `ppSymbol`  
 \[out\] Um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) o objeto que representa o símbolo no endereço especificado.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)