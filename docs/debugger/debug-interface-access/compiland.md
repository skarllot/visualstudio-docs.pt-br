---
title: "Compiland | Microsoft Docs"
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
  - "Símbolo compiland"
  - "compilandos, símbolo compiland"
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Compiland
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Existe uma `SymTagCompiland` de símbolos para cada Compiland vinculado ao arquivo. exe.  Compiland informações são divididas entre os símbolos com um `SymTagCompiland` marca, que pode ser recuperada sem carregar os símbolos compiland adicionais, e símbolos com um `SymTagCompilandDetails` marca, que pode exigir Carregando símbolos adicionais.  
  
## Propriedades  
 A tabela a seguir mostra as propriedades que são válidas para este tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|-----------------|-------------------|---------------|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE`Se o Edit and Continue foi habilitada na compilação.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo para o arquivo. exe.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID do símbolo pai lexical.|  
|[IDiaSymbol::get\_libraryName](../Topic/IDiaSymbol::get_libraryName.md)|`BSTR`|Nome do arquivo de biblioteca ou o objeto local a partir do qual objeto foi carregado.|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Nome do arquivo de objeto do compiland.|  
|[IDiaSymbol::get\_sourceFileName](../Topic/IDiaSymbol::get_sourceFileName.md)|`BSTR`|Nome do arquivo de origem.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice do símbolo.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retorna `SymTagCompiland` \(uma da [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores\).|  
  
## Consulte também  
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)   
 [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)   
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)