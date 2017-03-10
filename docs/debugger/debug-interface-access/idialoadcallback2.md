---
title: "IDiaLoadCallback2 | Microsoft Docs"
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
  - "Interface IDiaLoadCallback2"
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback2
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recebe retornos de chamada de procedimento de localização, permitindo que as restrições a serem impostas sobre o processo de localização o símbolo do DIA.  
  
## Sintaxe  
  
```  
IDiaLoadCallback2 : IDiaLoadCallback  
```  
  
## Métodos na ordem de Vtable  
 Com os métodos de [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) interface, essa interface expõe os métodos a seguir:  
  
|Método|Descrição|  
|------------|---------------|  
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|Determina se procurando um arquivo. PDB no diretório de depuração do original.|  
|[IDiaLoadCallback2::RestrictReferencePathAccess](../Topic/IDiaLoadCallback2::RestrictReferencePathAccess.md)|Determina se é permitida a procurar um arquivo. PDB no caminho onde o arquivo. exe está localizado.|  
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Determina se é permitida a procurando informações de depuração de arquivos. dbg.|  
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|Determina se é permitida a procura de arquivos. PDB no diretório raiz do sistema.|  
  
## Comentários  
 O aplicativo cliente implementa essa interface e fornece uma referência a ele na chamada para o [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.  Lembre\-se de implementar todos os métodos na [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) interface também.  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Consulte também  
 [Interfaces \(SDK de Acesso à Interface de Depuração\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)