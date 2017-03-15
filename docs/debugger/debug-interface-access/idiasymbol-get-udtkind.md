---
title: "IDiaSymbol::get_udtKind | Microsoft Docs"
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
  - "Método IDiaSymbol::get_udtKind"
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_udtKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera a variedade de um tipo definido pelo usuário \(UDT\).  
  
## Sintaxe  
  
```cpp#  
HRESULT get_udtKind (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um valor a partir do [Enumeração UdtKind](../../debugger/debug-interface-access/udtkind.md) enumeração que especifica o tipo de uma UDT: união, classe ou estrutura.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração UdtKind](../../debugger/debug-interface-access/udtkind.md)