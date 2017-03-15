---
title: "IDiaTable::get_Count | Microsoft Docs"
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
  - "Método IDiaTable::get_Count"
ms.assetid: bb47abe8-6706-4679-bc52-79f6444dae7e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaTable::get_Count
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o número de itens na tabela.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o número de itens na tabela.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)