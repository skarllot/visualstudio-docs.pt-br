---
title: "IDiaStackWalkHelper::readMemory | Microsoft Docs"
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
  - "Método IDiaStackWalkHelper2::readMemory"
ms.assetid: e1eb90aa-49b7-476c-9e70-7e8f08994cbe
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::readMemory
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lê um bloco de dados de imagem do executável na memória.  
  
## Sintaxe  
  
```cpp#  
HRESULT readMemory(   
   enum MemoryTypeEnum type,  
   ULONGLONG           va,  
   DWORD               cbData,  
   DWORD*              pcbData,  
   BYTE*               pbData  
);  
```  
  
#### Parâmetros  
 `type`  
 \[in\] Um valor a partir do [Enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md) enumeração que especifica o tipo de memória para ler.  
  
 VA  
 \[in\] Endereço virtual da imagem a partir do qual iniciar a leitura.  
  
 `cbData`  
 \[in\] O tamanho do buffer de dados em bytes.  
  
 `pcbData`  
 \[out\] Retorna o número de bytes lidos de fato.  Se `pbData` é `NULL`, e em seguida, este é o número total de bytes de dados disponíveis.  
  
 `pbData`  
 \[in, out\] Um buffer que é preenchido com a memória de leitura.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [Enumeração MemoryTypeEnum](../../debugger/debug-interface-access/memorytypeenum.md)