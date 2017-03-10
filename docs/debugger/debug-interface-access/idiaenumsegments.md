---
title: "IDiaEnumSegments | Microsoft Docs"
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
  - "Interface IDiaEnumSegments"
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSegments
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enumera os diversos segmentos contidos na fonte de dados.  
  
## Sintaxe  
  
```  
IDiaEnumSegments : IUnknown  
```  
  
## Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaEnumSegments`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaEnumSegments::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Recupera o [IEnumVARIANT Interface](http://msdn.microsoft.com/pt-br/139e3c93-faef-4003-9079-e0e94494db3e) versão deste enumerador.|  
|[IDiaEnumSegments::get\_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Recupera o número de segmentos.|  
|[IDiaEnumSegments::Item](../Topic/IDiaEnumSegments::Item.md)|Recupera um segmento por meio de um índice.|  
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Recupera um número especificado de segmentos na seqüência de enumeração.|  
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Ignora um número especificado de segmentos em uma seqüência de enumeração.|  
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Redefine uma seqüência de enumeração para o início.|  
|[IDiaEnumSegments::Clone](../Topic/IDiaEnumSegments::Clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
  
## Comentários  
  
## Observações para chamadores  
 Obter essa interface chamando o `QueryInterface` método em um [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto.  Consulte o exemplo para obter detalhes.  
  
## Exemplo  
 Este exemplo mostra como obter o `IDiaEnumSections` interface de uma tabela.  Para obter um exemplo mais completo do uso de segmentos, consulte o [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) interface.  
  
```cpp#  
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)  
{  
    CComPtr<IDiaEnumSegments> pSegments;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                __uuidof( IDiaEnumSegments ),  
                                (void**)&pSegments )  
                  )  
       )  
    {  
        // Do something with this enumeration  
    }  
}  
```  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Consulte também  
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)