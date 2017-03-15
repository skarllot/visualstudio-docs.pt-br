---
title: "IDiaSectionContrib::get_relocationsCrc | Microsoft Docs"
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
  - "Método IDiaSectionContrib::get_relocationsCrc"
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib::get_relocationsCrc
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera a verificação de redundância cíclica \(CRC\), as informações de realocação da seção.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_relocationsCrc (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o CRC as informações de realocação da seção.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há suporte para esta propriedade.  Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)