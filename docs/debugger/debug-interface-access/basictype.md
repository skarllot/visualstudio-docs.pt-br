---
title: "BasicType | Microsoft Docs"
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
  - "Enumeração BasicType"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica o tipo básico do símbolo.  
  
## Sintaxe  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## Elements  
 btNoType  
 Nenhum tipo básico for especificado.  
  
 btVoid  
 Tipo básico é um `void`.  
  
 btChar  
 Tipo básico é um `char` \(tipo de C\/C\+\+\).  
  
 btWChar  
 Tipo básico é um caractere de largo \(Unicode\) \(`WCHAR`\).  
  
 btInt  
 Tipo básico é `signed int` \(tipo de C\/C\+\+\).  
  
 btUInt  
 Tipo básico é `unsigned int` \(tipo de C\/C\+\+\).  
  
 btFloat  
 Tipo básico é um número de ponto flutuante \(`FLOAT`\).  
  
 btBCD  
 Tipo básico é um decimal codificado em binário \(`BCD`\).  
  
 btBool  
 Tipo básico é um booleano \(`BOOL`\).  
  
 btLong  
 Tipo básico é um `long int` \(tipo de C\/C\+\+\).  
  
 btULong  
 Tipo básico é um `unsigned long int` \(tipo de C\/C\+\+\).  
  
 btCurrency  
 Tipo básico é a moeda.  
  
 btDate  
 Tipo básico é data\/hora \(`DATE`\).  
  
 btVariant  
 Tipo básico é uma estrutura do tipo de variável \(`VARIANT`\).  
  
 btComplex  
 Tipo básico é um número complexo.  
  
 btBit  
 Tipo básico é um pouco.  
  
 btBSTR  
 Tipo básico é uma seqüência de caracteres básica ou binária \(`BSTR`\).  
  
 btHresult  
 Tipo básico é um `HRESULT`.  
  
## Comentários  
 Os valores desta enumeração são retornados pela [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) método.  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)