---
title: "DataKind | Microsoft Docs"
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
  - "Enumeração DataKind"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indica o escopo específico de um valor de dados.  
  
## Sintaxe  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Elements  
 DataIsUnknown  
 Símbolo de dados não pode ser determinado.  
  
 DataIsLocal  
 Item de dados é uma variável local.  
  
 DataIsStaticLocal  
 Item de dados é uma variável local estática.  
  
 DataIsParam  
 Item de dados é um parâmetro formal.  
  
 DataIsObjectPtr  
 Item de dados é um ponteiro de objeto \(`this`\).  
  
 DataIsFileStatic  
 Item de dados é uma variável de escopo do arquivo.  
  
 DataIsGlobal  
 Item de dados é uma variável global.  
  
 DataIsMember  
 Item de dados é uma variável de membro de objeto.  
  
 DataIsStaticMember  
 Item de dados é uma variável estática de classe.  
  
 DataIsConstant  
 Item de dados é um valor constante.  
  
## Comentários  
 Os valores desta enumeração são retornados pela [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) método.  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)