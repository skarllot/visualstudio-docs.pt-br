---
title: "IDiaSymbol::get_lexicalParent | Microsoft Docs"
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
  - "Método IDiaSymbol::get_lexicalParent"
ms.assetid: 4d119965-33a8-474c-9c64-95c5218c389c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_lexicalParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma referência ao pai do léxico do símbolo.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_lexicalParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) o objeto que representa o pai lexical do símbolo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 O pai lexical de um símbolo é a função de encerramento ou módulo.  Por exemplo, o pai lexical de um parâmetro de função ou variável local é a própria função enquanto o pai lexical da função é o módulo em que é definida.  
  
 Os símbolos possíveis que podem aparecer como pais lexicais estão documentados na [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md).  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Hierarquia lexical de tipos de símbolos](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)