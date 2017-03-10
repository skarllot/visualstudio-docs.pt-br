---
title: "Vis&#227;o geral (SDK de Acesso &#224; Interface de Depura&#231;&#227;o) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "tipos definidos pelo usuário"
  - "arquivos .dbg"
  - "módulos"
  - "interfaces [DIA SDK]"
  - "arquivos DBG"
  - "procedimentos [DIA SDK]"
  - "arquivos executáveis"
  - "Objetos COM, no DIA SDK"
  - "compilands"
  - "imagens executáveis"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vis&#227;o geral (SDK de Acesso &#224; Interface de Depura&#231;&#227;o)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Use o SDK do DIA para acessar as informações de depuração da Microsoft.  O SDK DIA fornece que um suplemento de COM base no conjunto de APIs que elimina a necessidade de reescrever o seu código sempre que a Microsoft altera o formato das informações de depuração.  O SDK DIA também permite que você leia a partir de um conjunto selecionado de versões anteriores de informações de depuração, localizados nos arquivos. PDB e DBG gerados pelo [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] versões 5.0 e posterior.  
  
 Cada interface no SDK DIA representa um objeto COM diferente, exceto onde indicado de outra forma.  Interfaces adicionais e, portanto, os objetos adicionais, são criados por meio de consultas explícitas, como [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) ou [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), em vez de chamar `QueryInterface` em ponteiros de interface existentes.  
  
## Consulte também  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)