---
title: "IDiaSymbol::get_typeIds | Microsoft Docs"
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
  - "Método IDiaSymbol::get_typeIds"
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma matriz de valores de identificador de tipo de compilador específico para esse símbolo.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### Parâmetros  
 `cTypeIds`  
 \[in\] Tamanho do buffer para armazenar os dados.  
  
 `pcTypeIds`  
 \[out\] Retorna o número de `typeIds` escrito, ou então, se `typeIds` é `NULL`, em seguida, o número total de identificadores de tipo disponíveis.  
  
 `typeIds[]`  
 \[out\] Uma matriz que deve ser preenchido com os identificadores de tipo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)