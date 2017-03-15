---
title: "Locais de s&#237;mbolos | Microsoft Docs"
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
  - "Valores LocationType"
  - "símbolos [DIA SDK] locais"
ms.assetid: 7c8cd8fe-169e-4161-9cff-5e9015984add
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Locais de s&#237;mbolos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

A maioria dos símbolos têm um local definido dentro do arquivo de imagem.  Local de um símbolo é especificado com um valor a partir do [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md) enumeração.  O símbolo pode suportar propriedades adicionais dependendo do local.  
  
 A tabela a seguir mostra os mais usados tipos de localização e suas propriedades adicionais.  
  
|Tipo de local|Propriedades adicionais|  
|-------------------|-----------------------------|  
|`LocIsNull`|Nenhum|  
|`LocIsStatic`|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)<br /><br /> [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)\(se estiverem ativados relativos endereços virtuais\)<br /><br /> [IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)\(se a base da imagem foi definido como diferente de zero\)|  
|`LocIsTLS`|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)<br /><br /> [IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|  
|`LocIsRegRel`|[IDiaSymbol::get\_registerId](../Topic/IDiaSymbol::get_registerId.md)<br /><br /> [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsThisRel`|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsEnregistered`|[IDiaSymbol::get\_registerId](../Topic/IDiaSymbol::get_registerId.md)|  
|`LocIsBitField`|[IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)<br /><br /> [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)<br /><br /> [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocIsSlot`|[IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|  
|`LocIsIlRel`|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|  
|`LocInMetaData`|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|  
|`LocIsConstant`|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|  
  
## Consulte também  
 [IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)   
 [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)   
 [IDiaSymbol::get\_registerId](../Topic/IDiaSymbol::get_registerId.md)   
 [IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)   
 [IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)   
 [IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)   
 [IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)   
 [IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Símbolos e marcas de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)