---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
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
  - "Método IDiaLoadCallback::NotifyDebugDir"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Chamado quando um diretório de depuração foi encontrado no arquivo. exe.  
  
## Sintaxe  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### Parâmetros  
 `fExecutable`  
 \[in\] `TRUE` se o diretório de depuração é lidos a partir de um arquivo executável \(em vez de um arquivo DBG\).  
  
 `cbData`  
 \[in\] Contagem de bytes de dados no diretório de depuração.  
  
 `data[]`  
 \[in\] Uma matriz que é preenchida com o diretório de depuração.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  O código de retorno costuma ser ignorado.  
  
## Comentários  
 O [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método chama esse retorno de chamada quando encontra um diretório de depuração ao processar o arquivo executável.  
  
 Esse método remove a necessidade de informações de depuração diferente da encontrada no arquivo. PDB de suporte ao cliente para o arquivo executável e\/ou depuração de engenharia reversa.  Com esses dados, o cliente pode reconhecer o tipo de informações de depuração disponíveis e se ele reside no arquivo executável ou o arquivo DBG.  
  
 A maioria dos clientes não necessitarão esse retorno de chamada porque o `IDiaDataSource::loadDataForExe` método transparente, abre arquivos. PDB e DBG tanto quando necessário para servir de símbolos.  
  
## Consulte também  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)