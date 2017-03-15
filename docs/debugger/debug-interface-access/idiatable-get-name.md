---
title: "IDiaTable::get_name | Microsoft Docs"
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
  - "Método IDiaTable::get_name"
ms.assetid: f6e9cd07-63cd-48a6-9835-e69c2d0859c5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaTable::get_name
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o nome da tabela.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_name (   
   BSTR* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o nome da tabela.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)