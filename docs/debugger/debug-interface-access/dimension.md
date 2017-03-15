---
title: "Dimens&#227;o | Microsoft Docs"
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
  - "Símbolo Dimension"
ms.assetid: 94f791da-bfea-454f-8a14-da31e8e1596a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Dimens&#227;o
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cada array FORTRAN tem uma dimensão que é identificada por um `SymTagDimension` símbolo.  
  
## Propriedades  
 A tabela a seguir mostra as propriedades adicionais de válido para este tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|-----------------|-------------------|---------------|  
|[IDiaSymbol::get\_lowerBound](../Topic/IDiaSymbol::get_lowerBound.md)|`IDiaSymbol*`|Limite inferior de uma dimensão de matriz do FORTRAN.|  
|[IDiaSymbol::get\_lowerBoundId](../Topic/IDiaSymbol::get_lowerBoundId.md)|`DWORD`|ID do símbolo o limite inferior.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice do símbolo.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retorna `SymTagDimension` \(uma da [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores\).|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|`IDiaSymbol*`|Limite superior de uma dimensão de matriz do FORTRAN.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|`DWORD`|ID do símbolo de limite superior.|  
  
## Consulte também  
 [ArrayType](../../debugger/debug-interface-access/arraytype.md)   
 [Hierarquia de classes de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)