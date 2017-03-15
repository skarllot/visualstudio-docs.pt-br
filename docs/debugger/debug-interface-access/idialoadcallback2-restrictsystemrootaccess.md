---
title: "IDiaLoadCallback2::RestrictSystemRootAccess | Microsoft Docs"
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
  - "Método IDiaLoadCallback2::RestrictSystemRootAccess"
ms.assetid: 39f22db8-632a-4ef0-babc-23f758e6d937
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2::RestrictSystemRootAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Determina se é permitida a procura de arquivos. PDB no diretório raiz do sistema.  
  
## Sintaxe  
  
```cpp#  
HRESULT RestrictSystemRootAccess();  
```  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Qualquer código de retorno diferente de `S_OK` impede que a pesquisa de raiz do sistema de arquivos. PDB.  
  
## Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)