---
title: "IDiaSourceFile::get_uniqueId | Microsoft Docs"
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
  - "Método IDiaSourceFile::get_uniqueId"
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um valor de chave de inteiros simples que é exclusivo para esta imagem.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um valor de chave de inteiros simples que é exclusivo para esta imagem.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Comparando as chaves em vez de seqüências de caracteres podem acelerar o processamento de número de linha.  
  
## Consulte também  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)