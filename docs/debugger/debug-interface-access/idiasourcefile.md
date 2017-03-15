---
title: "IDiaSourceFile | Microsoft Docs"
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
  - "Interface IDiaSourceFile"
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Representa um arquivo de origem.  
  
## Sintaxe  
  
```  
IDiaSourceFile : IUnknown  
```  
  
## Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDiaSourceFile`.  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaSourceFile::get\_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Recupera um valor de chave de inteiros simples que é exclusivo para esta imagem.|  
|[IDiaSourceFile::get\_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Recupera o nome do arquivo de origem.|  
|[IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Recupera o tipo de soma de verificação.|  
|[IDiaSourceFile::get\_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Recupera um enumerador dos compilandos com números de linha, fazendo referência a esse arquivo.|  
|[IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Recupera os bytes de soma de verificação.|  
  
## Comentários  
  
## Observações para chamadores  
 Obter essa interface chamando o [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) ou [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) métodos.  Consulte o exemplo para obter detalhes.  
  
## Exemplo  
 Esta função exibe os nomes de todos os arquivos de origem, contribuindo para a tabela especificada.  
  
```cpp#  
void ShowSourceFiles(IDiaTable *pTable)  
{  
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;  
    if ( SUCCEEDED( pTable->QueryInterface(  
                                _uuidof( IDiaEnumSourceFiles ),  
                               (void**)&pSourceFiles )  
                  )  
       )  
    {  
        CComPtr<IDiaSourceFile> pSourceFile;  
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&  
                celt == 1 )  
        {  
            CDiaBSTR fileName;  
            if ( pSourceFile->get_fileName( &fileName) == S_OK )  
            {  
                printf( "file name: %ws\n", fileName );  
            }  
            pSourceFile = NULL;  
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
 [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)   
 [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)   
 [IDiaLineNumber::get\_sourceFile](../Topic/IDiaLineNumber::get_sourceFile.md)   
 [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)   
 [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)   
 [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)