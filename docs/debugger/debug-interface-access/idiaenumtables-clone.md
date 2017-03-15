---
title: "IDiaEnumTables::Clone | Microsoft Docs"
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
  - "Método IDiaEnumTables::Clone"
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.  
  
## Sintaxe  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumTables** ppenum  
);  
```  
  
#### Parâmetros  
 `ppenum`  
 \[out\] Retorna um [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) objeto que contém uma duplicata do enumerador.  As tabelas não são duplicadas, apenas o enumerador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)