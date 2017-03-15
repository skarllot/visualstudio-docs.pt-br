---
title: "Constantes (SDK de Acesso &#224; Interface de Depura&#231;&#227;o) | Microsoft Docs"
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
  - "constantes, DIA SDK"
  - "DIA SDK, constantes"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Constantes (SDK de Acesso &#224; Interface de Depura&#231;&#227;o)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Essas constantes de seqüência de caracteres podem ser usados para identificar várias seções de um arquivo de banco de dados \(PDB\) de depuração do programa através do SDK do DIA.  
  
## Constantes  
 A seguir é declarada como macros C\/C\+\+.  
  
|Macro|Valor|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "Símbolos"|  
|`DiaTable_Sections`|L "Seções"|  
|`DiaTable_SrcFiles`|L "Arquivos de origem"|  
|`DiaTable_LineNums`|L "LineNumbers"|  
|`DiaTable_SegMap`|L "SegmentMap"|  
|`DiaTable_Dbg`|L "Dbg"|  
|`DiaTable_InjSrc`|L "InjectedSource"|  
|`DiaTable_FrameData`|L "FrameData"|  
  
## Exemplo  
 Aqui está um exemplo utilizando um dos seguintes símbolos:  
  
```cpp#  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## Requisitos  
 Cabeçalho: dia2.h  
  
## Consulte também  
 [Referência](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)