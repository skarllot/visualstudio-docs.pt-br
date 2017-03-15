---
title: "IDiaEnumSourceFiles | Microsoft Docs"
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
  - "Interface IDiaEnumSourceFiles"
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Enumera os diversos arquivos de origem contidos na fonte de dados.  
  
## Sintaxe  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaEnumSourceFiles`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaEnumSourceFiles::get\_\_NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Recupera o `IEnumVARIANT Interface` versão deste enumerador.|  
|[IDiaEnumSourceFiles::get\_Count](../Topic/IDiaEnumSourceFiles::get_Count.md)|Recupera o número de arquivos de origem.|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Recupera um arquivo de origem por meio de um índice.|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Recupera um número especificado de arquivos de origem na seqüência de enumeração.|  
|[IDiaEnumSourceFiles::Skip](../Topic/IDiaEnumSourceFiles::Skip.md)|Ignora um número especificado de arquivos de origem em uma seqüência de enumeração.|  
|[IDiaEnumSourceFiles::Reset](../Topic/IDiaEnumSourceFiles::Reset.md)|Redefine uma seqüência de enumeração para o início.|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.|  
  
## Comentários  
  
## Observações para chamadores  
 Obter essa interface chamando o `QueryInterface` método em um [IDiaTable](../../debugger/debug-interface-access/idiatable.md) objeto.  Consulte o exemplo para obter detalhes.  
  
## Exemplo  
 Este exemplo mostra como obter o `IDiaEnumSourceFiles` interface da lista de tabelas em um objeto de sessão do DIA.  Para obter um exemplo de acesso às informações de arquivo de origem, consulte o [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) interface.  
  
```cpp#  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
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
```  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Consulte também  
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)