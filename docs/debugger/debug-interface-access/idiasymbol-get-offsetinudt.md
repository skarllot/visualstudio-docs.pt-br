---
title: "IDiaSymbol::get_offsetInUdt | Microsoft Docs"
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
  - "Método IDiaSymbol::get_offsetInUdt"
ms.assetid: 442f20d9-9d6a-44a1-83fb-c3f8c14b6c97
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_offsetInUdt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o deslocamento para o início de um tipo definido pelo usuário \(UDT\) de um membro no UDT.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_offsetInUdt(   
   DWORD* pRetVal)  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o deslocamento em bytes do local do símbolo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 Essa função é usada somente em registros locais em uma compilação otimizada.  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)