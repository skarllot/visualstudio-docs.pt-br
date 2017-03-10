---
title: "IDiaEnumDebugStreamData::Item | Microsoft Docs"
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
  - "Método IDiaEnumDebugStreamData::Item"
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o registro especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parâmetros  
 índice  
 \[in\] Índice do registro a serem recuperados.  O índice está em um intervalo de 0 a `count`\-1, onde `count` é retornado por [IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md).  
  
 cbData diferente  
 \[in\] Tamanho do buffer de dados, em bytes.  
  
 pcbData  
 \[out\] Retorna o número de bytes retornados.  Se `data` é `NULL`, em seguida, `pcbData` contém o número total de bytes de dados disponíveis no registro especificado.  
  
 Data\]  
 \[out\] Um buffer que é preenchido com os dados de registro de fluxo de depuração.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  Retorna `E_INVALIDARG` de parâmetros inválidos e se a `index` parâmetro está fora dos limites.  
  
## Consulte também  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [IDiaEnumDebugStreams::Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreamData::get\_Count](../Topic/IDiaEnumDebugStreamData::get_Count.md)   
 [IDiaEnumDebugStreamData::Skip](../Topic/IDiaEnumDebugStreamData::Skip.md)