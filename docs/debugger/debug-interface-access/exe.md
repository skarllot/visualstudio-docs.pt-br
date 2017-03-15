---
title: "Exe | Microsoft Docs"
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
  - "Arquivos .dll"
  - "Símbolo Exe"
  - "Arquivos .exe"
  - "arquivos executáveis, símbolo Exe"
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Exe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Exe é o único símbolo sem que seja um léxico ou classe pai, pois representa o escopo global do arquivo. exe ou. dll.  Há apenas um símbolo com o `SymTagExe` marca por arquivo.  O [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md) método retorna o símbolo.  
  
## Propriedades  
 A tabela a seguir mostra as propriedades que são válidas para este tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|-----------------|-------------------|---------------|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Idade deste executável.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID`deste executável.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE`Se o arquivo de símbolo associado a este executável contém tipos C \(apenas no v 8.0 do SDK DIA ou posterior\).|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE`Se os símbolos privados tem sido removidos o arquivo de símbolo associado a este executável \(somente no v 8.0 do SDK DIA ou posterior\).|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Valor que indica a CPU de destino \(uma da [Enumeração CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) valores\).|  
|[IDiaSymbol::get\_name](../Topic/IDiaSymbol::get_name.md)|`BSTR`|Nome do arquivo. exe.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Assinatura do executável.|  
|[IDiaSymbol::get\_symbolsFileName](../Topic/IDiaSymbol::get_symbolsFileName.md)|`BSTR`|Caminho completo para o arquivo. pdb ou DBG do arquivo. exe.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice do símbolo.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retorna `SymTagExe` \(uma da [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores\).|  
  
## Consulte também  
 [IDiaSession::get\_globalScope](../Topic/IDiaSession::get_globalScope.md)   
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)