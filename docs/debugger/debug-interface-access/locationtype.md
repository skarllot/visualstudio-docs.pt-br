---
title: "LocationType | Microsoft Docs"
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
  - "Enumeração LocationType"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indica o tipo de informação de local contido em um símbolo.  
  
## Sintaxe  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## Elements  
 `LocIsNull`  
 Informações sobre o local não está disponível.  
  
 `LocIsStatic`  
 O local é estático.  
  
 `LocIsTLS`  
 Local está no armazenamento local de segmento.  
  
 `LocIsRegRel`  
 O local é relativo ao registro.  
  
 `LocIsThisRel`  
 O local é `this`\-relativo.  
  
 `LocIsEnregistered`  
 Localização é um registro.  
  
 `LocIsBitField`  
 Localização é um campo de bits.  
  
 `LocIsSlot`  
 O local é um slot de Microsoft Intermediate Language \(MSIL\).  
  
 `LocIsIlRel`  
 O local é relativo a MSIL.  
  
 `LocInMetaData`  
 Local está nos metadados.  
  
 `LocIsConstant`  
 Localização é um valor constante.  
  
 `LocTypeMax`  
 O número de tipos de localização desta enumeração.  
  
## Comentários  
 As propriedades disponíveis para o [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) interface dependem do local do símbolo dentro do arquivo de imagem.  Para obter mais informações, consulte [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md).  
  
 Os valores desta enumeração são retornados por uma chamada para o [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md) método.  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)   
 [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)