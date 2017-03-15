---
title: "IDiaDataSource::openSession | Microsoft Docs"
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
  - "Método IDiaDataSource::openSession"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abre uma sessão para consultar os símbolos.  
  
## Sintaxe  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### Parâmetros  
 ppSession  
 \[out\] Retorna um [IDiaSession](../../debugger/debug-interface-access/idiasession.md) objeto que representa a sessão aberta.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  A tabela a seguir mostra os valores de retorno possíveis para esse método.  
  
|Valor|Descrição|  
|-----------|---------------|  
|E\_UNEXPECTED|O [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) objeto anteriormente não foi inicializado com uma fonte de símbolos.|  
|E\_INVALIDARG|Inválido `ppSession` parâmetro.|  
|E\_OUTOFMEMORY|Memória insuficiente para abrir a sessão.|  
  
## Comentários  
 Esse método abre um [IDiaSession](../../debugger/debug-interface-access/idiasession.md) o objeto para uma fonte de dados.  
  
 `IDiaSession`objetos implementam consultas na fonte de dados.  Uma sessão gerencia um espaço de endereço para cada conjunto de símbolos de depuração.  Se o arquivo. exe ou. dll, descrito pelos símbolos de fonte de dados está ativo no endereço vários intervalos \(por exemplo, porque vários processos que ele carregado\), uma sessão para cada intervalo de endereço deve ser usada.  
  
## Exemplo  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## Consulte também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Visão Geral](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)