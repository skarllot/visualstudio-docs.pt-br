---
title: "IDiaLoadCallback::NotifyOpenPDB | Microsoft Docs"
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
  - "Método IDiaLoadCallback::NotifyOpenPDB"
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyOpenPDB
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chamado quando o candidato a abrir um arquivo. PDB.  
  
## Sintaxe  
  
```cpp#  
HRESULT NotifyOpenPDB (   
   LPCOLESTR pdbPath,  
   HRESULT   resultCode  
);  
```  
  
#### Parâmetros  
 `pdbPath`  
 \[in\] O caminho completo do arquivo. PDB.  
  
 `resultCode`  
 \[in\] Código que indica o sucesso \(`S_OK`\) ou falha da carga como aplicada a este arquivo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  O código de retorno costuma ser ignorado.  
  
## Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)