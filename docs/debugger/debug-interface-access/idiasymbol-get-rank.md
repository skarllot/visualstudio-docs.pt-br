---
title: "IDiaSymbol::get_rank | Microsoft Docs"
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
  - "Método IDiaSymbol::get_rank"
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_rank
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera a posição \(número de dimensões\) de uma matriz multidimensional do FORTRAN.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o número de dimensões em uma matriz multidimensional do FORTRAN.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 Classificação indica o número de dimensões em uma matriz em que a matriz é declarada como `myarray[1,2,3]`.  Este exemplo tem uma classificação de dimensões de 3 e 3.  Classificação não se aplica ao C\+\+ que usa o conceito de uma matriz de matrizes para cada dimensão \(ou seja, `myarray[1][2][3]`\).  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)