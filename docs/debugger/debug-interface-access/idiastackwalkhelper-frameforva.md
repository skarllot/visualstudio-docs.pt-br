---
title: "IDiaStackWalkHelper::frameForVA | Microsoft Docs"
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
  - "Método IDiaStackWalkHelper2::frameForVA"
ms.assetid: f35fc61b-f8dd-473a-b583-82c304059422
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::frameForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o quadro de pilha que contém o endereço virtual especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT frameForVA(   
   ULONGLONG        va,  
   IDiaFrameData**  ppFrame  
);  
```  
  
#### Parâmetros  
 `va`  
 \[in\] O endereço virtual para os dados do quadro.  
  
 `ppFrame`  
 \[out\] Um [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) o objeto que representa o quadro de pilha no endereço especificado.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)