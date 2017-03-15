---
title: "IDiaAddressMap::get_imageAlign | Microsoft Docs"
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
  - "Método IDiaAddressMap::get_imageAlign"
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::get_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o alinhamento da imagem atual.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o valor de alinhamento da imagem do executável.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Imagens são alinhadas em limites de memória específica, dependendo de como a imagem foi carregada e criada.  O alinhamento é normalmente nos limites de 1, 2, 4, 8, 16, 32 ou 64 bytes.  O alinhamento da imagem pode ser definido com uma chamada para o [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) método.  
  
## Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)