---
title: "IDiaEnumSectionContribs | Microsoft Docs"
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
  - "Interface IDiaEnumSectionContribs"
ms.assetid: 0d6c0632-310f-4a99-8921-58149a1817e3
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSectionContribs
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enumera as contribuições de seção diversos contidas na fonte de dados.  
  
## Sintaxe  
  
```  
IDiaEnumSectionContribs : IUnknown  
```  
  
## Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaEnumSectionContribs`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaEnumSectionContribs::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-newenum.md)|Recupera o [IEnumVARIANT Interface](http://msdn.microsoft.com/pt-br/139e3c93-faef-4003-9079-e0e94494db3e) versão deste enumerador.|  
|[IDiaEnumSectionContribs::get\_Count](../Topic/IDiaEnumSectionContribs::get_Count.md)|Recupera o número de contribuições de seção.|  
|[IDiaEnumSectionContribs::Item](../../debugger/debug-interface-access/idiaenumsectioncontribs-item.md)|Recupera as contribuições de seção por meio de um índice.|  
|[IDiaEnumSectionContribs::Next](../Topic/IDiaEnumSectionContribs::Next.md)|Recupera um número especificado de contribuições de seção na seqüência de enumeração.|  
|[IDiaEnumSectionContribs::Skip](../Topic/IDiaEnumSectionContribs::Skip.md)|Ignora um número especificado de contribuições de seção em uma seqüência de enumeração.|  
|[IDiaEnumSectionContribs::Reset](../../debugger/debug-interface-access/idiaenumsectioncontribs-reset.md)|Redefine uma seqüência de enumeração para o início.|  
|[IDiaEnumSectionContribs::Clone](../../debugger/debug-interface-access/idiaenumsectioncontribs-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
  
## Comentários  
  
## Observação para chamadores  
 Obter a interface da [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) método.  Consulte o exemplo para obter detalhes.  
  
## Exemplo  
 Este exemplo mostra como obter \(o `GetEnumSectionContribs` função\) e usar \(o `ShowSectionContribs` função\) a `IDiaEnumSectionContribs` interface.  Para obter um exemplo mais completo do uso de contribuições de seção, consulte a [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md) interface.  
  
```cpp#  
  
      IDiaEnumSectionContribs* GetEnumSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pUnknown    = NULL;  
    REFIID                   iid         = __uuidof(IDiaEnumSectionContribs);  
    IDiaEnumTables*          pEnumTables = NULL;  
    IDiaTable*               pTable      = NULL;  
    ULONG                    celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
  
void ShowSectionContribs(IDiaSession *pSession)  
{  
    IDiaEnumSectionContribs* pEnumSectionContribs;  
  
    pEnumSectionContribs = GetEnumSectionContribs(pSession);  
    if (pSectionContrib != NULL)  
    {  
        IDiaSectionContrib* pSectionContrib;  
        ULONG celt = 0;  
  
        while(pEnumSectionContribs->Next(1, &pSectionContrib, &celt) == S_OK &&  
              celt == 1)  
        {  
            PrintSectionContrib(pSectionContrib, pSession);  
            pSectionContrib->Release();  
        }  
        pSectionContrib->Release();   
    }  
}  
```  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Consulte também  
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)