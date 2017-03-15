---
title: "CV_access_e | Microsoft Docs"
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
  - "Enumeração CV_access_e"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica o escopo de visibilidade \(nível de acesso\) de variáveis e funções de membro.  
  
## Sintaxe  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## Elements  
 CV\_private  
 Membro tem acesso privado.  
  
 CV\_protected  
 Membro tem protegidos de acesso.  
  
 CV\_public  
 Membro tem acesso público.  
  
## Comentários  
 O `friend` especificador de acesso não é incluída aqui porque ele é normalmente usado por funções não\-membros que têm acesso aos elementos particulares e protegidos da classe.  Use o [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) método para encontrar símbolos com `SymTagFriend` acesso.  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)