---
title: "IDiaEnumDebugStreamData::Next | Microsoft Docs"
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
  - "Método IDiaEnumDebugStreamData::Next"
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um número especificado de registros na seqüência enumerado.  
  
## Sintaxe  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### Parâmetros  
 celt  
 \[in\] O número de registros a serem recuperados.  
  
 cbData diferente  
 \[in\] Tamanho do buffer de dados, em bytes.  
  
 pcbData  
 \[out\] Retorna o número de bytes retornados.  Se `data` for NULL, em seguida, `pcbData` contém o número total de bytes de dados disponíveis para todos os registros de solicitados.  
  
 Data\]  
 \[out\] Um buffer que deve ser preenchido com os dados de registro de fluxo de depuração.  
  
 pceltFetched  
 \[in, out\] Retorna o número de registros em `data`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há mais registros.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)