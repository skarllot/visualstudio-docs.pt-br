---
title: "IDiaInjectedSource::get_source | Microsoft Docs"
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
  - "Método IDiaInjectedSource::get_source"
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera os bytes de código fonte.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parâmetros  
 `cbData`  
 \[in\] O número de bytes que representa o tamanho do buffer de dados.  
  
 `pcbData`  
 \[out\] Retorna o número de bytes que representa os bytes retornados.  Se `data` é `NULL`, em seguida, `pcbData` é o número total de bytes de dados disponíveis.  
  
 `data[]`  
 \[out\] Um buffer que deve ser preenchido com os bytes de código\-fonte.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há suporte para esta propriedade.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)