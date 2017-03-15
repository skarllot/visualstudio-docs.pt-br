---
title: "IDiaFrameData::get_addressOffset | Microsoft Docs"
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
  - "Método IDiaFrameData::get_addressOffset"
ms.assetid: b68e2e68-6483-4936-bf97-1b0a13cb75e2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_addressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera a compensação parte do endereço do código para o quadro.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna a parte de compensação do endereço do código para o quadro.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há suporte para esta propriedade.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)