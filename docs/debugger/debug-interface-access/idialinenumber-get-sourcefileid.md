---
title: "IDiaLineNumber::get_sourceFileId | Microsoft Docs"
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
  - "Método IDiaLineNumber::get_sourceFileId"
ms.assetid: 4f482a1e-e85f-4173-98de-8e5f7622554b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLineNumber::get_sourceFileId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um identificador de arquivo de origem de forma exclusiva para o arquivo de origem que contribuíram com esta linha.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_sourceFileId (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o identificador de arquivo de origem de forma exclusiva para o arquivo de origem que contribuíram com esta linha.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há suporte para esta propriedade.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)