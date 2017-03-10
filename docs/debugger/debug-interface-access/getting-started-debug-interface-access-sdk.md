---
title: "Guia de Introdu&#231;&#227;o (SDK de Acesso &#224; Interface de Depura&#231;&#227;o) | Microsoft Docs"
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
  - "arquivos .dbg"
  - "arquivos DBG"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Guia de Introdu&#231;&#227;o (SDK de Acesso &#224; Interface de Depura&#231;&#227;o)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

O Debug Interface Access \(DIA\) SDK fornece a você com documentação das instruções e um exemplo que ilustra como usar a API do DIA.  Use os métodos e interfaces no SDK do DIA para desenvolver aplicativos personalizados que abra os arquivos. PDB e DBG e procure o seu conteúdo para símbolos, valores, atributos, endereços e outras informações de depuração.  Esse SDK também fornece tabelas de referência para as propriedades associadas a símbolos encontrados em aplicativos C\+\+.  
  
 Para melhor usar o SDK DIA, você deve estar familiarizado com o seguinte:  
  
-   Linguagem de programação C\+\+  
  
-   Programação COM  
  
-   Ambiente de desenvolvimento integrado de Visual Studio \(IDE\) para compilar as amostras  
  
 O SDK DIA normalmente é instalado com o Visual Studio e seu local padrão é  *\[drive\]*\\Arquivos de Programas\\Microsoft Visual Studio 9.0\\DIA SDK.  Como parte da instalação, o MSDIA90. dll, que implementa o SDK DIA, é registrado automaticamente para que tudo o que você precisa fazer para usá\-lo é incluir `dia2.h` em seu programa e um link para `diaguids.lib`.  
  
 Cabeçalho: include\\dia2.h  
  
 Biblioteca: lib\\diaguids.lib  
  
 DLL: bin\\msdia80.dll  
  
 IDL: idl\\dia2.idl  
  
## Nesta seção  
 [Visão Geral](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Revisa a arquitetura básica do dia.  
  
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fornece instruções passo a passo sobre como usar a API do DIA para consultar um arquivo. PDB.  
  
## Consulte também  
 [SDK de Acesso à Interface de Depuração](../../debugger/debug-interface-access/debug-interface-access-sdk.md)