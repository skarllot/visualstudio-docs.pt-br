---
title: "IDiaEnumSourceFiles::Item | Microsoft Docs"
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
  - "Método IDiaEnumSourceFiles::Item"
ms.assetid: 3c19d7ed-0232-4b0e-9b10-f33ed9e0c93b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSourceFiles::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um arquivo de origem por meio de um índice.  
  
## Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD            index,  
   IDiaSourceFile** sourceFile  
);  
```  
  
#### Parâmetros  
 índice  
 \[in\] Índice da [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) o objeto a ser recuperado.  O índice está em um intervalo de 0 a `count`\-1, onde `count` é retornado pelo [IDiaEnumSourceFiles::get\_Count](../Topic/IDiaEnumSourceFiles::get_Count.md) método.  
  
 sourceFile  
 \[out\] Retorna um [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) objeto representando o arquivo de fonte desejado.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)