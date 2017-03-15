---
title: "FuncDebugEnd | Microsoft Docs"
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
  - "Símbolo FuncDebugEnd"
  - "depuração de ponto de extremidade [DIA SDK]"
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# FuncDebugEnd
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Se uma função tiver um ponto definido no qual a depuração é finalizar, o ponto de partida de depuração é identificada por um símbolo com um `SymTagFuncDebugEnd` marca.  
  
## Propriedades  
 A tabela a seguir mostra as propriedades que são válidas para este tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|-----------------|-------------------|---------------|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Deslocamento de parte do local. Para obter detalhes, consulte a [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte da seção de local; Para obter detalhes, consulte a [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Se a função usa uma convenção de chamada personalizada \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Se a função realiza um retorno distante \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Se a função contém um retorno de interrupção \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`Se a função é estática \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo da função de encerramento.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID do símbolo pai lexical.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|Tem de pontos de extremidade estático local; Para obter detalhes, consulte [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Se a função foi especificada com o [noinline](/visual-cpp/cpp/noinline) atributo \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Se a função foi especificada com o [noreturn](/visual-cpp/cpp/noreturn) atributo \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Se a função nunca é chamada \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Deslocamento do símbolo na memória; Para obter detalhes, consulte a [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Se a função tem informações de depuração para código otimizado \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice do símbolo.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posição relativa do final dessa função dentro de seu módulo.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retorna `SymTagFuncDebugEnd` \(uma da [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores\).|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posição dessa função dentro da imagem executável.|  
  
## Consulte também  
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)