---
title: "IDiaEnumSymbols | Microsoft Docs"
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
  - "Interface IDiaEnumSymbols"
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbols
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enumera os vários símbolos contidos na fonte de dados.  
  
## Sintaxe  
  
```  
IDiaEnumSymbols : IUnknown  
```  
  
## Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaEnumSymbols`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaEnumSymbols::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Recupera o `IEnumVARIANT Interface` versão deste enumerador.|  
|[IDiaEnumSymbols::get\_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Recupera o número de símbolos.|  
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Recupera um símbolo por meio de um índice.|  
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Recupera um número especificado de símbolos na seqüência de enumeração.|  
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Ignora um número especificado de símbolos em uma seqüência de enumeração.|  
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Redefine uma seqüência de enumeração para o início.|  
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
  
## Comentários  
 Essa interface fornece símbolos agrupados por um tipo específico de símbolo, por exemplo, `SymTagUDT` \(tipos definidos pelo usuário\) ou `SymTagBaseClass`.  Para trabalhar com símbolos agrupados por endereço, use o [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md) interface.  
  
## Observações para chamadores  
 Para obter essa interface chamando os métodos a seguintes:  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
-   [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)  
  
## Exemplo  
 Este exemplo mostra como obter o `IDiaEnumSymbols` interface e, em seguida, use essa enumeração para tipos definidos pelo usuário da lista \(UDTs\).  
  
> [!NOTE]
>  `CDiaBSTR`é uma classe que encapsula um `BSTR` e trata automaticamente liberando a seqüência de caracteres quando a instanciação sai do escopo.  
  
```cpp#  
void ShowUDTs(IDiaSymbol *pGlobals)  
{  
    CComPtr<IDiaEnumSymbols> pEnum;  
    CComPtr<IDiaSymbol> pSymbol;  
    HRESULT hr;  
  
    hr = pGlobals->findChildren(SymTagUDT,  
                                NULL,  
                                nsfCaseInsensitive | nsfUndecoratedName,  
                                &pEnum);  
    if (hr == S_OK)  
    {  
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR name;  
            if ( pSymbol->get_name( &name ) != S_OK )  
                Fatal( "get_name" );  
            printf( "Found UDT: %ws\n", name );  
            pSymbol = 0;  
        }  
    }  
}  
```  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Consulte também  
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)