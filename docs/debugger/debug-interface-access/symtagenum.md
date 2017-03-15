---
title: "SymTagEnum | Microsoft Docs"
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
  - "Enumeração SymTagEnum"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica o tipo de símbolo.  
  
## Sintaxe  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## Elements  
 `SymTagNull`  
 Indica que o símbolo não tem nenhum tipo.  
  
 `SymTagExe`  
 Indica que o símbolo é um arquivo. exe.  Existe apenas um `SymTagExe` símbolo por armazenamento de símbolo.  Ele serve como o escopo global e não tem um pai léxico.  
  
 `SymTagCompiland`  
 Indica o símbolo compiland para cada componente compiland do armazenamento de símbolo.  Para aplicativos nativos, `SymTagCompiland` símbolos correspondem aos arquivos de objeto vinculados na imagem.  Para alguns tipos de imagens da Microsoft Intermediate Language \(MSIL\), há um compiland por classe.  
  
 `SymTagCompilandDetails`  
 Indica que o símbolo contém atributos estendidos do compiland.  Recuperar essas propriedades pode exigir Carregando símbolos compiland.  
  
 `SymTagCompilandEnv`  
 Indica que o símbolo é uma seqüência de caracteres de ambiente definida para o compiland.  
  
 `SymTagFunction`  
 Indica que o símbolo é uma função.  
  
 `SymTagBlock`  
 Indica que o símbolo é um bloco aninhado.  
  
 `SymTagData`  
 Indica que o símbolo de dados.  
  
 `SymTagAnnotation`  
 Indica que o símbolo de uma anotação de código.  Filhos desse símbolo são seqüências de dados constante \(`SymTagData`, `LocIsConstant`, `DataIsConstant`\).  A maioria dos clientes ignorar esse símbolo.  
  
 `SymTagLabel`  
 Indica que o símbolo é um rótulo.  
  
 `SymTagPublicSymbol`  
 Indica que o símbolo é um símbolo público.  Para aplicativos nativos, esse símbolo é o símbolo externo COFF encontrado ao vincular a imagem.  
  
 `SymTagUDT`  
 Indica que o símbolo é um tipo definido pelo usuário \(estrutura, classe ou união\).  
  
 `SymTagEnum`  
 Indica que o símbolo é uma enumeração.  
  
 `SymTagFunctionType`  
 Indica que o símbolo é um tipo de assinatura de função.  
  
 `SymTagPointerType`  
 Indica que o símbolo é um tipo de ponteiro.  
  
 `SymTagArrayType`  
 Indica que o símbolo é um tipo de matriz.  
  
 `SymTagBaseType`  
 Indica que o símbolo é um tipo base.  
  
 `SymTagTypedef`  
 Indica que o símbolo é um `typedef`, ou seja, um alias para outro tipo.  
  
 `SymTagBaseClass`  
 Indica que o símbolo é uma classe base de um tipo definido pelo usuário.  
  
 `SymTagFriend`  
 Indica que o símbolo é um amigo de um tipo definido pelo usuário.  
  
 `SymTagFunctionArgType`  
 Indica que o símbolo é um argumento de função.  
  
 `SymTagFuncDebugStart`  
 Indica que o símbolo é a localização final do código de prólogo da função.  
  
 `SymTagFuncDebugEnd`  
 Indica que o símbolo é o local de início do código de epílogo da função.  
  
 `SymTagUsingNamespace`  
 Indica que o símbolo é um nome de espaço para nome ativo no escopo atual.  
  
 `SymTagVTableShape`  
 Indica que o símbolo é uma descrição de tabela virtual.  
  
 `SymTagVTable`  
 Indica que o símbolo é um ponteiro de tabela virtual.  
  
 `SymTagCustom`  
 Indica que o símbolo é um símbolo personalizado e não é interpretado por dia.  
  
 `SymTagThunk`  
 Indica que o símbolo é uma conversão usada para compartilhamento de dados entre 16 e 32 bits.  
  
 `SymTagCustomType`  
 Indica que o símbolo é um símbolo de compilador personalizado.  
  
 `SymTagManagedType`  
 Indica que o símbolo de metadados.  
  
 `SymTagDimension`  
 Indica que o símbolo é uma matriz multidimensional do FORTRAN.  
  
 `SymTagCallSite`  
 Indica que o símbolo representa o local de chamada.  
  
 `SymTagInlineSite`  
 Indica que o símbolo representa o site embutido.  
  
 `SymTagBaseInterface`  
 Indica que o símbolo é uma interface base.  
  
 `SymTagVectorType`  
 Indica que o símbolo é um tipo de vetor.  
  
 `SymTagMatrixType`  
 Indica que o símbolo é um tipo de matriz.  
  
 `SymTagHLSLType`  
 Indica que o símbolo é um tipo de linguagem de Shader de nível alto.  
  
## Comentários  
 Todos os símbolos dentro de um arquivo de depuração tem uma marca de identificação que especifica o tipo do símbolo.  
  
 Os valores desta enumeração são retornados por uma chamada para o [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md) método.  
  
 Os valores desta enumeração são passados para os seguintes métodos para limitar o escopo da pesquisa a um tipo específico de símbolo:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../Topic/IDiaSession::findSymbolByRVA.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../Topic/IDiaSession::findSymbolByVA.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)