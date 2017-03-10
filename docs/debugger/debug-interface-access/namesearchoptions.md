---
title: "NameSearchOptions | Microsoft Docs"
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
  - "Enumeração NameSearchOptions"
ms.assetid: 67dfbede-2678-47df-b664-5c49841d0b9b
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# NameSearchOptions
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica as opções de pesquisa para nomes de arquivo e o símbolo.  
  
## Sintaxe  
  
```cpp#  
enum NameSearchOptions {   
   nsNone,  
   nsfCaseSensitive     = 0x1,  
   nsfCaseInsensitive   = 0x2,  
   nsfFNameExt          = 0x4,  
   nsfRegularExpression = 0x8,  
   nsfUndecoratedName   = 0x10,  
  
// For backward compatibility:  
   nsCaseSensitive           = nsfCaseSensitive,  
   nsCaseInsensitive         = nsfCaseInsensitive,  
   nsFNameExt                = nsfCaseInsensitive | nsfFNameExt,  
   nsRegularExpression       = nsfRegularExpression | nsfCaseSensitive,  
   nsCaseInRegularExpression = nsfRegularExpression | nsfCaseInsensitive  
};  
```  
  
## Elements  
 `nsNone`  
 Nenhuma opção seja especificada.  
  
 `nsfCaseSensitive`  
 Aplica\-se uma correspondência de nome diferencia maiúsculas de minúsculas.  
  
 `nsfCaseInsensitive`  
 Aplica\-se uma correspondência de maiúsculas e minúsculas do nome.  
  
 `nsfFNameExt`  
 Trata de nomes como caminhos e aplica uma correspondência de nome filename. ext.  
  
 `nsfRegularExpression`  
 Aplica\-se uma correspondência de nome diferencia maiúsculas de minúsculas, usando asteriscos \(\*\) e pontos de interrogação \(?\) como curingas.  
  
 `nsfUndecoratedName`  
 Aplica\-se somente a símbolos que têm ambos não decorados e decorada nomes.  
  
## Comentários  
 Os valores desta enumeração são passados para os seguintes métodos:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Requisitos  
 Cabeçalho: dia2.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)