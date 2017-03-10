---
title: "IDiaEnumSourceFiles::Next | Microsoft Docs"
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
  - "Método IDiaEnumSourceFiles::Next"
ms.assetid: 83bf6317-ff39-4c5c-8987-cba34e7a6983
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSourceFiles::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um número especificado de arquivos de origem na seqüência de enumeração.  
  
## Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG            celt,  
   IDiaSourceFile** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
#### Parâmetros  
 celt  
 \[in\] O número de arquivos de origem do enumerador a serem recuperados.  
  
 rgelt  
 \[out\]Uma matriz que deve ser preenchido com o [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objetos que representam os arquivos de fonte desejado.  
  
 pceltFetched  
 \[out\] Retorna o número de arquivos de origem do enumerador buscadas.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não houver nenhum mais arquivos de origem.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)