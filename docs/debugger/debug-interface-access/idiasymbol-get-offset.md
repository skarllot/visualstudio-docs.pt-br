---
title: "IDiaSymbol::get_offset | Microsoft Docs"
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
  - "Método IDiaSymbol::get_offset"
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o deslocamento do local do símbolo.  Use when the [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) is `LocIsRegRel` or `LocIsBitField`.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o deslocamento em bytes do local do símbolo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 O deslocamento é de algum ponto conhecido previamente determinado.  Por exemplo, o deslocamento para um `LocIsBitField` tipo de local é normalmente desde o início da classe que contém.  
  
## Requisitos  
  
|Requisito|Descrição|  
|---------------|---------------|  
|Cabeçalho:|dia2.h|  
|Versão:|Versão 7.0 do SDK DIA|  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)