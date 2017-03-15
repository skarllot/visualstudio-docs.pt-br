---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
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
  - "Método IDiaDataSource::get_lastError"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o nome de arquivo para o último erro de carga.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### Parâmetros  
 pRetVal  
 \[out\] Retorna um string que contém o nome de arquivo. PDB associado com o último erro de carga.  
  
## Valor de retorno  
 Retorna o último código de erro causado por uma operação de carregamento.  Retorna `E_INVALIDARG` se a `pRetVal` parâmetro é `NULL`.  
  
## Exemplo  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)