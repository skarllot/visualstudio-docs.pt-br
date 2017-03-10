---
title: "CompilandDetails | Microsoft Docs"
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
  - "Símbolo CompilandDetails"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Compiland informações são divididas entre os símbolos com um `SymTagCompiland` marca \(detalhes de baixa\) e um `SymTagCompilandDetails` marca \(alta detalhes\).  `SymTagCompilandDetails`requer Carregando símbolos adicionais.  No entanto, ele fornece uma ampla gama de informações sobre o compiland que não está disponível com um `SymTagCompiland` símbolo.  
  
## Propriedades  
 A tabela a seguir mostra as propriedades que são válidas para este tipo de símbolo.  
  
|Propriedade|Tipo de dados|Descrição|  
|-----------------|-------------------|---------------|  
|[IDiaSymbol::get\_backEndBuild](../Topic/IDiaSymbol::get_backEndBuild.md)|`DWORD`|Número de compilação de back\-end do compilador.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Número de versão principal do back\-end do compilador.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Número de versão secundária do back\-end do compilador.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nome do compilador que produziu este compiland \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_editAndContinueEnabled](../Topic/IDiaSymbol::get_editAndContinueEnabled.md)|`BOOL`|`TRUE`Se editar e continuar foram ativadas na compilação.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Número de compilação de front\-end do compilador.|  
|[IDiaSymbol::get\_frontEndMajor](../Topic/IDiaSymbol::get_frontEndMajor.md)|`DWORD`|Número de versão principal de front\-end do compilador.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Número de versão secundária front\-end do compilador.|  
|[IDiaSymbol::get\_hasDebugInfo](../Topic/IDiaSymbol::get_hasDebugInfo.md)|`BOOL`|`TRUE`Se este compiland tem informações de depuração \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE`Se este compiland contém o código gerenciado \(somente no v 8.0 do SDK DIA ou posterior\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE`Se o compiland foi compilado com o [\/GS \(verificação de segurança do buffer\)](/visual-cpp/build/reference/gs-buffer-security-check) o comutador de compilador \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE`Se compiland foi convertido a partir do código de idioma comum intermediário \(CIL\) para código nativo.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE`Se tipos definidos pelo usuário \(UDT\) tem sido alinhados à alguns especificado o limite de memória \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_isHotpatchable](../Topic/IDiaSymbol::get_isHotpatchable.md)|`BOOL`|`TRUE`Se compiland foi compilado com o [\/hotpatch \(Criar imagem hotpatchable\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) o comutador de compilador \(somente no v 8.0 do SDK DIA ou posterior\).|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE`Se compiland foi compilado com o [\/LTCG \(geração de código do tempo de vinculação\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) o comutador de compilador \(somente no v 8.0 SDK do DIA ou posterior\).|  
|[IDiaSymbol::get\_isMSILNetmodule](../Topic/IDiaSymbol::get_isMSILNetmodule.md)|`BOOL`|TRUE se compiland é um módulo de Microsoft Intermediate Language \(MSIL\) \(somente no v 8.0 do SDK DIA ou posterior\).|  
|[IDiaSymbol::get\_language](../Topic/IDiaSymbol::get_language.md)|`DWORD`|Idioma de código de origem.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Símbolo para o compiland.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID do símbolo pai lexical.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Plataforma em que o compiland foi compilado \(dentre as [Enumeração CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) valores\).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID de índice do símbolo.|  
|[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)|`DWORD`|Retorna `SymTagCompilandDetails` \(uma da [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valores\).|  
  
## Comentários  
 Geralmente, os compiladores vêm em um formulário, conhecido como um compilador de duas passagens; em algumas versões do compilador, cada passagem é tratada por um programa separado.  Eles são conhecidos como compiladores de front\-end e back\-end, respectivamente, portanto, as propriedades do símbolo para números de versão de back\-end e front\-end.  
  
## Consulte também  
 [Compiland](../../debugger/debug-interface-access/compiland.md)   
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)