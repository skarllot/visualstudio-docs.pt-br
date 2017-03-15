---
title: "IDiaSymbol::get_unmodifiedType | Microsoft Docs"
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
  - "Método IDiaSymbol::get_unmodifiedType"
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_unmodifiedType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o tipo original para esse símbolo.  Use quando o [Enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) é definida como um tipo.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) o objeto que representa o tipo original deste símbolo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retornará `S_FALSE` ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de `S_FALSE` significa que a propriedade não está disponível para o símbolo.  
  
## Comentários  
 O tipo atual é uma modificação do tipo retornado original.  O tipo original de um símbolo pode ser determinado pelo primeiro obtendo o tipo do símbolo e, em seguida, interrogar que retornou um tipo para o tipo original.  Observe que alguns símbolos podem não ter um tipo de modificação do tipo original.  
  
## Requisitos  
 Cabeçalho: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia100.dll  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)