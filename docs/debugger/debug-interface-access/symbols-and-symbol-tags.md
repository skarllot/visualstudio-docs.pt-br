---
title: "S&#237;mbolos e marcas de s&#237;mbolos | Microsoft Docs"
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
  - "símbolos [DIA SDK]"
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# S&#237;mbolos e marcas de s&#237;mbolos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Informações de depuração sobre um programa compilado são armazenadas no arquivo de banco de dados \(. PDB\) de programa, como símbolos que podem ser acessados usando as APIs do SDK do Debug Interface Access \(DIA\).  Todos os símbolos têm um [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) e um [IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) propriedade.  O `symTag` propriedade indica o tipo de símbolo, conforme definido pela [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração.  O `symIndexId` propriedade é um `DWORD` valor que contém o identificador exclusivo para cada instância de um símbolo.  
  
 Símbolos também têm propriedades que podem especificar informações adicionais sobre o símbolo, bem como referências a outros símbolos, com freqüência um [IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) ou [IDiaSymbol::get\_classParent](../Topic/IDiaSymbol::get_classParent.md).  Quando você consulta uma propriedade que contém uma referência, a referência é retornada como um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto.  Tais propriedades são sempre combinadas com outra propriedade com o mesmo nome mas suffixed com "Id", por exemplo, [IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [IDiaSymbol::get\_classParentId](../Topic/IDiaSymbol::get_classParentId.md).  As tabelas no [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md), [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), e [Hierarquia de classes de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) as propriedades de estrutura de tópicos para cada um dos diferentes tipos de símbolos.  Essas propriedades podem ter informações relevantes sobre ou referências a outros símbolos.  Porque o `*Id` propriedades são identificadores de ordinais simplesmente numéricos de suas propriedades relacionadas, eles são omitidos de discussões ainda mais.  Eles são chamados somente onde são necessárias para fins de esclarecimento de parâmetro.  
  
 Ao tentar acessar a propriedade, se nenhum erro ocorrer e a propriedade de símbolo foi atribuída um valor, a propriedade "get" método retorna `S_OK`.  Um valor de retorno de `S_FALSE` indica que a propriedade não é válida para o símbolo atual.  
  
## Nesta seção  
 [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)  
 Descreve os diferentes tipos de locais de que um símbolo pode ter.  
  
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Descreve os tipos de símbolos que formam as hierarquias lexicais como, por exemplo, arquivos, módulos e funções.  
  
 [Hierarquia de classes de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Descreve os tipos de símbolos que correspondem aos elementos de idioma diferente, como tipos de retorno da função, matrizes e classes.  
  
## Consulte também  
 [SDK de Acesso à Interface de Depuração](../../debugger/debug-interface-access/debug-interface-access-sdk.md)