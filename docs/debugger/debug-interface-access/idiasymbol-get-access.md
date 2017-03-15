---
title: "IDiaSymbol::get_access | Microsoft Docs"
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
  - "Método IDiaSymbol::get_access"
ms.assetid: 908976ae-95c4-4020-89c9-de137f727f98
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_access
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o modificador de acesso de um membro da classe.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_access (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um valor a partir do [Enumeração CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md) enumeração que especifica o modificador de acesso de um membro da classe.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Requisitos  
  
|Requisito|Descrição|  
|---------------|---------------|  
|Cabeçalho:|dia2.h|  
|Versão:|Versão 7.0 do SDK DIA|  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md)