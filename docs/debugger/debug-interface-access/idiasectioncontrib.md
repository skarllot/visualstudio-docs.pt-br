---
title: "IDiaSectionContrib | Microsoft Docs"
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
  - "Interface IDiaSectionContrib"
ms.assetid: 371d40f6-ca0e-4d7e-9210-64d3768996c6
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSectionContrib
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera dados de descrevendo uma contribuição de seção, ou seja, um bloco contíguo de memória contribuíram para a imagem por um compiland.  
  
## Sintaxe  
  
```  
IDiaSectionContrib : IUnknown  
```  
  
## Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaSectionContrib`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaSectionContrib::get\_compiland](../../debugger/debug-interface-access/idiasectioncontrib-get-compiland.md)|Recupera uma referência para o símbolo de compiland que contribuíram nesta seção.|  
|[IDiaSectionContrib::get\_addressSection](../../debugger/debug-interface-access/idiasectioncontrib-get-addresssection.md)|Recupera a parte da seção de endereço da contribuição.|  
|[IDiaSectionContrib::get\_addressOffset](../../debugger/debug-interface-access/idiasectioncontrib-get-addressoffset.md)|Recupera a compensação parte do endereço da contribuição.|  
|[IDiaSectionContrib::get\_relativeVirtualAddress](../Topic/IDiaSectionContrib::get_relativeVirtualAddress.md)|Recupera o imagem endereço virtual relativo \(RVA\) de contribuição.|  
|[IDiaSectionContrib::get\_virtualAddress](../../debugger/debug-interface-access/idiasectioncontrib-get-virtualaddress.md)|Recupera o endereço virtual \(VA\) de contribuição.|  
|[IDiaSectionContrib::get\_length](../../debugger/debug-interface-access/idiasectioncontrib-get-length.md)|Recupera o número de bytes em uma seção.|  
|[IDiaSectionContrib::get\_notPaged](../../debugger/debug-interface-access/idiasectioncontrib-get-notpaged.md)|Recupera um sinalizador que indica se a seção não pode ser paginada memória insuficiente.|  
|[IDiaSectionContrib::get\_nopad](../../debugger/debug-interface-access/idiasectioncontrib-get-nopad.md)|Recupera um sinalizador que indica se a seção não deve ser preenchida para o próximo limite de memória.|  
|[IDiaSectionContrib::get\_code](../Topic/IDiaSectionContrib::get_code.md)|Recupera um sinalizador que indica se a seção contém código executável.|  
|[IDiaSectionContrib::get\_code16bit](../../debugger/debug-interface-access/idiasectioncontrib-get-code16bit.md)|Recupera um sinalizador que indica se a seção contém código de 16 bits.|  
|[IDiaSectionContrib::get\_initializedData](../../debugger/debug-interface-access/idiasectioncontrib-get-initializeddata.md)|Recupera um sinalizador que indica se a seção contém dados inicializados.|  
|[IDiaSectionContrib::get\_uninitializedData](../Topic/IDiaSectionContrib::get_uninitializedData.md)|Recupera um sinalizador que indica se a seção contém dados não inicializados.|  
|[IDiaSectionContrib::get\_informational](../../debugger/debug-interface-access/idiasectioncontrib-get-informational.md)|Recupera um sinalizador que indica se uma seção contém comentários ou informações semelhantes.|  
|[IDiaSectionContrib::get\_remove](../../debugger/debug-interface-access/idiasectioncontrib-get-remove.md)|Recupera um sinalizador que indica se a seção deve é removida antes que ele é parte da imagem na memória.|  
|[IDiaSectionContrib::get\_comdat](../../debugger/debug-interface-access/idiasectioncontrib-get-comdat.md)|Recupera um sinalizador que indica se a seção é um registro COMDAT.|  
|[IDiaSectionContrib::get\_discardable](../../debugger/debug-interface-access/idiasectioncontrib-get-discardable.md)|Recupera um sinalizador que indica se a seção pode ser descartada.|  
|[IDiaSectionContrib::get\_notCached](../../debugger/debug-interface-access/idiasectioncontrib-get-notcached.md)|Recupera um sinalizador que indica se a seção não pode ser armazenado em cache.|  
|[IDiaSectionContrib::get\_share](../../debugger/debug-interface-access/idiasectioncontrib-get-share.md)|Recupera um sinalizador que indica se a seção pode ser compartilhada na memória.|  
|[IDiaSectionContrib::get\_execute](../../debugger/debug-interface-access/idiasectioncontrib-get-execute.md)|Recupera um sinalizador que indica se a seção é executável como código.|  
|[IDiaSectionContrib::get\_read](../../debugger/debug-interface-access/idiasectioncontrib-get-read.md)|Recupera um sinalizador que indica se a seção pode ser lido.|  
|[IDiaSectionContrib::get\_write](../../debugger/debug-interface-access/idiasectioncontrib-get-write.md)|Recupera um sinalizador que indica se a seção pode ser gravada.|  
|[IDiaSectionContrib::get\_dataCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-datacrc.md)|Recupera a verificação de redundância cíclica \(CRC\) dos dados na seção.|  
|[IDiaSectionContrib::get\_relocationsCrc](../../debugger/debug-interface-access/idiasectioncontrib-get-relocationscrc.md)|Recupera o CRC as informações de realocação da seção.|  
|[IDiaLineNumber::get\_compilandId](../../debugger/debug-interface-access/idialinenumber-get-compilandid.md)|Recupera o identificador de compiland para a seção.|  
  
## Comentários  
  
## Observações para chamadores  
 Essa interface é obtida chamando o [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md) e [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md) métodos.  Consulte o [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) interface para obter um exemplo de como obter o `IDiaSectionContrib` interface.  
  
## Exemplo  
 Esta função mostra o endereço de cada seção juntamente com quaisquer símbolos associados.  Consulte o [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) interface para ver como o `IDiaSectionContrib` interface é obtida.  
  
```cpp#  
void PrintSectionContrib(IDiaSectionContrib* pSecContrib, IDiaSession* pSession)  
{  
    if (pSecContrib != NULL && pSession != NULL)  
    {  
        DWORD rva;  
        if ( pSecContrib->get_relativeVirtualAddress( &rva ) == S_OK )  
        {  
            printf( "\taddr: 0x%.8X", rva );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                        name != NULL ? name : L"",  
                        szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
        }  
        else  
        {  
            DWORD isect;  
            DWORD offset;  
            pSecContrib->get_addressSection( &isect );  
            pSecContrib->get_addressOffset( &offset );  
            printf( "\taddr: 0x%.4X:0x%.8X", isect, offset );  
            pSecContrib = NULL;  
            CComPtr<IDiaSymbol> pSym;  
            if ( SUCCEEDED( psession->findSymbolByAddr(  
                                              isect,  
                                              offset,  
                                              SymTagNull,  
                                              &pSym )  
                          )  
               )  
            {  
                CDiaBSTR name;  
                DWORD    tag;  
                pSym->get_symTag( &tag );  
                pSym->get_name( &name );  
                printf( "     symbol: %ws (%ws)\n",  
                    name != NULL ? name : L"",  
                    szTags[ tag ] );  
            }  
            else  
            {  
                printf( "<no symbol found?>\n" );  
            }  
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
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)   
 [IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)