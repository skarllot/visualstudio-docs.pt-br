---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
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
  - "Método IDiaReadExeAtRVACallback::ReadExecutableAtRVA"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lê o número especificado de bytes, começando o especificado endereço virtual relativo \(RVA\) do arquivo executável.  
  
## Sintaxe  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parâmetros  
 `relativeVirtualAddress`  
 \[in\] RVA no arquivo executável para iniciar a leitura.  
  
 `cbData`  
 \[in\] Número de bytes a serem lidos.  
  
 `pcbData`  
 \[out\] Retorna o número de bytes lidos.  
  
 `data[]`  
 \[in, out\] Uma matriz que é preenchida com bytes lidos do arquivo.  
  
## Comentários  
 Este método é chamado pelo código de suporte do DIA para carregar os bytes de dados de um executável usando um endereço virtual relativo.  Este método é chamado para oferecer suporte a [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  
  
## Consulte também  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)