---
title: "IDiaSymbol::get_farReturn | Microsoft Docs"
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
  - "Método IDiaSymbol::get_farReturn"
ms.assetid: 141df0e9-f4d9-4330-a043-5d9ea865257f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_farReturn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um sinalizador que especifica se a função contém um retorno distante.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_farReturn(  
   BOOL *pFlag  
);  
```  
  
#### Parâmetros  
 `pFlag`  
 \[in\] Retorna `TRUE` se a função usa o retorno distante, caso contrário, retornará `FALSE`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Requisitos  
  
|Requisito|Descrição|  
|---------------|---------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V 8.0 do SDK DIA|  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)