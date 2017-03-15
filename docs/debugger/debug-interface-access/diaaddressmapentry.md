---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "Enumeração DiaAddressMapEntry"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Descreve uma entrada em um mapa do endereço.  
  
## Sintaxe  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Elements  
 `rva`  
 Um endereço virtual relativo \(RVA\) na imagem a.  
  
 `rvaTo`  
 O endereço virtual relativo `rva` é mapeado para a imagem de b.  
  
## Comentários  
 Um mapa de endereço fornece uma tradução do layout de uma imagem \(A\) para outro \(B\).  Uma matriz de `DiaAddressMapEntry` estruturas classificadas por `rva` define um mapa do endereço.  
  
 Para traduzir um endereço, `addrA`, na imagem a um endereço, `addrB`, na imagem B, execute as seguintes etapas:  
  
1.  Pesquisar o mapa da entrada, `e`, com os maiores `rva` menor ou igual a `addrA`.  
  
2.  Set `delta = addrA – e.rva`.  
  
3.  Set `addrB = e.rvaTo + delta`.  
  
 Uma matriz de `DiaAddressMapEntry` estruturas é passada para o [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## Requisitos  
 Cabeçalho: dia2.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)