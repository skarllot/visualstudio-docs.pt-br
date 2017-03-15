---
title: "IDiaImageData::get_imageBase | Microsoft Docs"
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
  - "Método IDiaImageData::get_imageBase"
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o local da memória onde a imagem deve ser baseada.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o valor de base da imagem sugeridas.  
  
## Valor de retorno  
 Se for bem\-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## Comentários  
 Devido a conflitos de base da imagem, uma imagem pode ser rebasing automaticamente em um local de memória não usada quando ele é carregado. Esse método retorna a dica de base \(local de memória sugerido\) que foi armazenada no módulo em tempo de compilação.  
  
## Consulte também  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)