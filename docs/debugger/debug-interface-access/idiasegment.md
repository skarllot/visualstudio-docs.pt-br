---
title: "IDiaSegment | Microsoft Docs"
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
  - "Interface IDiaSegment"
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mapeia os dados contra o número de seção para segmentos de espaço de endereço.  
  
## Sintaxe  
  
```  
IDiaSegment : IUnknown  
```  
  
## Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaSegment`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaSegment::get\_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Recupera o número de segmento.|  
|[IDiaSegment::get\_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Recupera o deslocamento em segmentos onde a seção começa.|  
|[IDiaSegment::get\_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Recupera o número de bytes no segmento.|  
|[IDiaSegment::get\_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Recupera um sinalizador que indica se o segmento pode ser lido.|  
|[IDiaSegment::get\_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Recupera um sinalizador que indica se o segmento pode ser modificado.|  
|[IDiaSegment::get\_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Recupera um sinalizador que indica se o segmento é executável.|  
|[IDiaSegment::get\_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Recupera o número de seção que mapeia para esse segmento.|  
|[IDiaSegment::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Recupera o endereço virtual relativo \(RVA\) do início da seção.|  
|[IDiaSegment::get\_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Recupera o endereço virtual \(VA\) do início da seção.|  
  
## Comentários  
 Como o SDK DIA já realiza traduções do deslocamento de seção para endereços virtuais relativos, a maioria dos aplicativos não fará uso das informações no mapa do segmento.  
  
## Observações para chamadores  
 Obter essa interface chamando o [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md) ou [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md) métodos.  Consulte o exemplo para obter detalhes.  
  
## Exemplo  
 Esta função exibe o endereço de todos os segmentos em uma tabela e o símbolo mais próximo.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSegments ),  
                               (void**)&pSegments )  
                  )  
       )  
    {  
        CComPtr<IDiaSegment> pSegment;  
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&  
                celt == 1 )  
        {  
            DWORD rva;  
            DWORD seg;  
  
            pSegment->get_addressSection( &seg );  
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )  
            {  
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );  
                pSegment = NULL;  
  
                CComPtr<IDiaSymbol> pSym;  
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )  
                {  
                    CDiaBSTR name;  
                    DWORD    tag;  
  
                    pSym->get_symTag( &tag );  
                    pSym->get_name( &name );  
                    printf( "\tClosest symbol: %ws (%ws)\n",  
                            name != NULL ? name : L"",  
                            szTags[ tag ] );  
                }  
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
 [IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)   
 [IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)