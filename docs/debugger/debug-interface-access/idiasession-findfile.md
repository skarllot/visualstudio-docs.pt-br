---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "Método IDiaSession::findFile"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recuperar arquivos de origem pelo compiland e nome.  
  
## Sintaxe  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### Parâmetros  
 `pCompiland`  
 \[in\] um objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o compiland a ser usado como um contexto para a pesquisa.  Defina o parâmetro como `NULL` para localizar arquivos de origem em todos os compilands.  
  
 `name`  
 \[in\] especifica o nome do arquivo de origem para ser recuperado.  Defina o parâmetro como `NULL` para que todos os arquivos de origem sejam recuperados.  
  
 `option`  
 \[in\] especifica as opções de comparação aplicadas para nomear a pesquisa.  Os valores da enumeração de [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) podem ser usados apenas ou em combinação.  
  
 `ppResult`  
 \[out\] retorna um objeto de [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) que contém uma lista dos arquivos de origem recuperados.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Exemplo  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## Consulte também  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)