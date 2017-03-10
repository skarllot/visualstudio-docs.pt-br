---
title: "IDiaSession::symbolById | Microsoft Docs"
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
  - "Método IDiaSession::symbolById"
ms.assetid: 062e4b5a-9c4d-4703-88da-ec13102c2b66
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::symbolById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera um símbolo por seu identificador exclusivo.  
  
## Sintaxe  
  
```cpp#  
HRESULT symbolById (   
   DWORD        id,  
   IDiaSymbol** ppSymbol  
);  
```  
  
#### Parâmetros  
 `id`  
 \[in\] Identificador exclusivo.  
  
 `ppSymbol`  
 \[out\] Retorna um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) recuperado do objeto que representa o símbolo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 O identificador especificado é um valor exclusivo usado internamente pelo SDK do DIA para fazer com que todos os símbolos exclusivo.  
  
 Esse método pode ser usado, por exemplo, para recuperar o símbolo que representa o tipo de outro símbolo \(veja o exemplo\).  
  
## Exemplo  
 Este exemplo recupera uma [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa o tipo de outro símbolo.  Este exemplo mostra como usar o `symbolById` método na sessão.  Uma abordagem mais simples é chamar o [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md) método para recuperar o símbolo de tipo diretamente.  
  
```cpp#  
IDiaSymbol *GetSymbolType(IDiaSymbol *pSymbol, IDiaSession *pSession)  
{  
    IDiaSymbol *pTypeSymbol = NULL;  
    if (pSymbol != NULL && pSession != NULL)  
    {  
        DWORD symbolTypeId;  
        pSymbol->get_typeId(&symbolTypeId);  
        pSession->symbolById(symbolTypeId, &pTypeSymbol);  
    }  
    return(pTypeSymbol);  
}  
```  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)