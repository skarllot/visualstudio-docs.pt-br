---
title: "IDiaLoadCallback::RestrictSymbolServerAccess | Microsoft Docs"
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
  - "Método IDiaLoadCallback::RestrictSymbolServerAccess"
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::RestrictSymbolServerAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Determina se o acesso será permitido para um servidor de símbolos para resolver os símbolos.  
  
## Sintaxe  
  
```cpp#  
HRESULT RestrictSymbolServerAccess();  
```  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Qualquer código de retorno diferente de `S_OK` impede o uso de um servidor de símbolos para resolver os símbolos.  
  
## Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)