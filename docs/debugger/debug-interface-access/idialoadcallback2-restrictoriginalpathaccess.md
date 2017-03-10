---
title: "IDiaLoadCallback2::RestrictOriginalPathAccess | Microsoft Docs"
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
  - "Método IDiaLoadCallback2::RestrictOriginalPathAccess"
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Determina se deve procurar um arquivo. PDB no diretório de depuração do original.  
  
## Sintaxe  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Qualquer código de retorno diferente de `S_OK` impede procurando um arquivo. PDB no diretório de depuração do original.  O diretório de depuração original é o caminho para o arquivo de símbolo compilado no executável quando a depuração está ativado.  Esse caminho não é necessariamente o mesmo que o caminho onde o executável existe.  
  
## Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)