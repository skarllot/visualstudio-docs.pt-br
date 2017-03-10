---
title: "IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressSection"
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retorna a parte da seção do endereço inicial do intervalo em que o símbolo de local é válido.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### Parâmetros  
 `section`  
 \[out\] Retorna a parte da seção do intervalo de endereços inicial.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
> [!NOTE]
>  Um código de erro retornado significa que o símbolo não tem informações sobre o intervalo ao vivo.  
  
## Comentários  
 O endereço formado pela seção e deslocamento é o início do intervalo em que o símbolo é válido.  
  
 Para obter o deslocamento parte do endereço, use [IDiaSymbol::get\_liveRangeStartAddressOffset](../Topic/IDiaSymbol::get_liveRangeStartAddressOffset.md).  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)