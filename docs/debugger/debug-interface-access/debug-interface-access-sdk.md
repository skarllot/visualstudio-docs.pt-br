---
title: "SDK de Acesso &#224; Interface de Depura&#231;&#227;o | Microsoft Docs"
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
  - "depuração [DIA SDK]"
  - "depurador [DIA SDK]"
  - "DIA SDK"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SDK de Acesso &#224; Interface de Depura&#231;&#227;o
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

O Microsoft Debug Interface Access Software Development Kit \(SDK DIA\) fornece acesso a informações armazenadas em arquivos de banco de dados \(. PDB\) do programa gerados pelas ferramentas de postcompiler Microsoft de depuração.  Porque o formato do arquivo. PDB gerado pelas ferramentas de postcompiler é submetido a revisão constante, expondo o formato é impraticável.  Usando a API do DIA, você pode desenvolver aplicativos que pesquisar e procurar informações de depuração, armazenadas em um arquivo. PDB.  Esses aplicativos poderiam, por exemplo, relatar informações de retorno de rastreamento de pilha e analisar dados de desempenho.  
  
## Nesta seção  
 [Guia de Introdução](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Fornece uma visão geral sobre o SDK DIA recursos e especifica onde o SDK DIA está instalado, bem como o cabeçalho necessário e os arquivos de biblioteca.  
  
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fornece instruções sobre como usar a API do DIA para consultar o arquivo. PDB.  
  
 [Símbolos e marcas de símbolos](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Discute como as marcas de símbolo e símbolos são usadas na API do DIA.  
  
 [Referência](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contém as interfaces, métodos, enumerações e estruturas da API do DIA.  
  
 [Exemplo de Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Ilustra como usar a API do DIA para pesquisar e procurar informações de depuração.  
  
 [Arquivo de origem Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 O código usado por fonte [Exemplo de Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) para demonstrar a API do DIA.