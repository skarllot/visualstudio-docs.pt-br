---
title: "CV_CFL_LANG | Microsoft Docs"
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
  - "Enumeração CV_CFL_LANG"
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_CFL_LANG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica o idioma de código fonte do aplicativo ou do módulo vinculado.  
  
## Sintaxe  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## Elements  
 CV\_CFL\_C  
 Idioma do aplicativo é c.  
  
 CV\_CFL\_CXX  
 Idioma do aplicativo é C\+\+.  
  
 CV\_CFL\_FORTRAN  
 Idioma do aplicativo é FORTRAN.  
  
 CV\_CFL\_MASM  
 Idioma do aplicativo é Microsoft Macro Assembler.  
  
 CV\_CFL\_PASCAL  
 Idioma do aplicativo é Pascal.  
  
 CV\_CFL\_BASIC  
 Idioma do aplicativo é BASIC.  
  
 CV\_CFL\_COBOL  
 Idioma do aplicativo é COBOL.  
  
 CV\_CFL\_LINK  
 Aplicativo é um módulo gerado pelo vinculador.  
  
 CV\_CFL\_CVTRES  
 Aplicativo é um módulo de recurso convertido com ferramenta CVTRES.  
  
 CV\_CFL\_CVTPGD  
 Aplicativo é um módulo POGO otimizado gerado com a ferramenta CVTPGD.  
  
 CV\_CFL\_CSHARP  
 Idioma do aplicativo é C\#.  
  
 CV\_CFL\_VB  
 Idioma do aplicativo é Visual Basic.  
  
 CV\_CFL\_ILASM  
 Idioma do aplicativo é o assembly de linguagem intermediária \(isto é, o Common Language Runtime \(CLR\) assembly\).  
  
 CV\_CFL\_JAVA  
 Idioma do aplicativo é Java.  
  
 CV\_CFL\_JSCRIPT  
 Idioma do aplicativo é Jscript.  
  
 CV\_CFL\_MSIL  
 Idioma do aplicativo é um desconhecido idioma MSIL \(Microsoft Intermediate\), possivelmente um resultado do uso de [\/LTCG \(geração de código do tempo de vinculação\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) alternar.  
  
 CV\_CFL\_HLSL  
 Idioma do aplicativo é o alto nível de sombreador idioma.  
  
## Comentários  
 Os valores desta enumeração são retornados por uma chamada para o [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md) método.  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)