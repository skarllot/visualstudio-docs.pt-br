---
title: "IDiaSession::findAcceleratorInlineesByName | Microsoft Docs"
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
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retorna uma enumeração de símbolos de quadros internos que correspondem ao nome da função in\-line especificado.  
  
## Sintaxe  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### Parâmetros  
 `name`  
 \[in\] o nome da função de inlinee a ser pesquisada.  
  
 `option`  
 \[in\] as opções de pesquisa de nome ser usado para procurar pelos quadros internos que correspondem a `name`.  Para mais informações, consulte [Enumeração NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 \[out\] um ponteiro à um ponteiro de interface de `IDiaEnumSymbols` que é inicializada com o resultado.  
  
## Valor de retorno  
 Se com êxito, retorna `S_OK`; caso contrário, retorna um código de erro.  
  
## Comentários  
 Essa função procura por inlinees somente dentro das funções de stub de aceleração.  Ignora registros nativos do procedimento C\+\+.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)