---
title: "IDiaSymbol::get_objectPointerType | Microsoft Docs"
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
  - "Método IDiaSymbol::get_objectPointerType"
ms.assetid: bce193b9-67b0-4c35-96e5-6a664937322e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_objectPointerType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o tipo de ponteiro de objeto para um método de classe.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_objectPointerType (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) o objeto que representa o ponteiro de objeto para um método de classe.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 Esta propriedade se aplica somente a símbolos com um [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) tipo de `SymTagFunctionType`.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)