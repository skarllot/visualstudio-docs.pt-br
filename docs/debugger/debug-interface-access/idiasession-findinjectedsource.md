---
title: "IDiaSession::findInjectedSource | Microsoft Docs"
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
  - "Método IDiaSession::findInjectedSource"
ms.assetid: 907531b6-1ef8-4153-986d-b72611a1632d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma lista de fontes que foram colocada no armazenamento de símbolo por provedores de atributo ou outros componentes do processo de compilação.  
  
## Sintaxe  
  
```cpp#  
HRESULT findInjectedSource (   
   LPCOLESTR                 srcFile,  
   IDiaEnumInjectedSources** ppResult  
);  
```  
  
#### Parâmetros  
 srcFile  
 \[in\] Nome do arquivo de origem que deseja pesquisar.  
  
 ppResult  
 \[out\] Retorna um [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) o objeto que contém uma lista de todas as fontes injetadas.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)