---
title: "Function (SDK de Acesso &#224; Interface de Depura&#231;&#227;o) | Microsoft Docs"
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
  - "Símbolo Function"
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Function (SDK de Acesso &#224; Interface de Depura&#231;&#227;o)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cada função é identificada por um `SymTagFunction` símbolo.  
  
## Propriedades  
 A tabela a seguir mostra as propriedades que são válidas para este tipo de símbolo.  
  
|Propriedade|`Data type`|Descrição|  
|-----------------|-----------------|---------------|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Um dos valores da [Enumeração CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md), se a função é uma função de membro.|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Deslocamento de parte do local. Para obter detalhes, consulte a [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte da seção de local; Para obter detalhes, consulte a [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md)|`IDiaSymbol*`|Símbolo para a classe, se a função é uma função de membro.|  
|[IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md)|`DWORD`|ID do símbolo classe pai.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`Se a função está marcada como uma constante.|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Se a função usa uma convenção de chamada personalizada \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Se a função executa um retorno distante \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_hasAlloca](../Topic/IDiaSymbol::get_hasAlloca.md)|`BOOL`|`TRUE`Se a função usa a função de memória alocada \(uinnder v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE`Se a função contém \(somente no v 8.0 SDK do DIA ou posterior\) de manipulação de exceção de estilo C\+\+.|  
|[IDiaSymbol::get\_hasEHa](../Topic/IDiaSymbol::get_hasEHa.md)|`BOOL`|`TRUE`Se a função contém o tratamento de exceção assíncrona \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE`Se a função contém assembly embutido \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE`Se a função contém um [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) de chamada \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`Se a função contém as verificações de segurança \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE`Se a função contém \(somente no v 8.0 SDK do DIA ou posterior\) de manipulação de exceção estruturada de estilo de Win32.|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE`Se a função contém um [setjmp](/visual-cpp/c-runtime-library/reference/setjmp) de chamada \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Se a função tem um retorno de interrupção \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE`Se uma função for intro virtual.|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE`Se a função tiver sido marcada com um do [inline, \_\_inline, \_\_forceinline](../../misc/inline-inline-forceinline.md) atributos.|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE`Se a função estiver marcada com o [naked](/visual-cpp/cpp/naked-cpp) atributo \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE`Se a função é estática \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Número de bytes de código de função, a partir do local.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo do delimitador compiland.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID do símbolo pai lexical.|  
|[IDiaSymbol::get\_locationType](../Topic/IDiaSymbol::get_locationType.md)|`DWORD`|As funções podem ter estático ou metadados locais; Para obter detalhes, consulte [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Nome da função.|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Se a função não é uma função embutida \(v somente n DIA SDK 8.0 ou posterior\).|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Se a função não está acessível \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Se a função não retorna um valor \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_noStackOrdering](../Topic/IDiaSymbol::get_noStackOrdering.md)|`BOOL`|`TRUE`Se a função foi compilada com verificações de segurança de buffer, mas nenhuma ordem de pilha pode ser feito.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Se o código possui informações de depuração para código otimizado \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE`Se a função é puramente virtual.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posição relativa desta função dentro de seu módulo.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice do símbolo.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retorna `SymTagFunction` \(uma da [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores\).|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Token de metadados para a função.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Símbolo de assinatura de função.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID do símbolo de tipo.|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`Se a função é não alinhada.|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|O formulário não decorado do nome da função \(somente no v 8.0 do SDK DIA ou posterior\)|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|Parte ou todo o formulário não decorado do nome da função \(somente no v 8.0 do SDK DIA ou posterior\).|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE`Se uma função virtual.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posição dessa função dentro da imagem executável.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Se uma função virtual, em seguida, o deslocamento da tabela de função virtual.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`Se a função está marcada como volátil.|  
  
## Consulte também  
 [Enumeração CV\_access\_e](../../debugger/debug-interface-access/cv-access-e.md)   
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [Enumeração LocationType](../../debugger/debug-interface-access/locationtype.md)   
 [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)