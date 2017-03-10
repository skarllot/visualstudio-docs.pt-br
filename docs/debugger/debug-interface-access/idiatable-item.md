---
title: "IDiaTable::Item | Microsoft Docs"
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
  - "Método IDiaTable::Item"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera uma referência à entrada na tabela especificada.  
  
## Sintaxe  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### Parâmetros  
 `index`  
 \[in\] O índice da entrada tabela no intervalo de 0 a `count`\-1, onde `count` é retornado pelo [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)método.  
  
 `element`  
 \[out\] Retorna um `IUnknown` o objeto que representa a entrada da tabela especificada.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Uma tabela representa uma coleção de objetos.  Dependendo desses objetos, o parâmetro de elemento pode ser convertido para a interface apropriada.  Por exemplo, se uma tabela contém [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) objetos, e em seguida, o parâmetro de elemento pode ser convertido para o `IDiaSegment` interface.  
  
 É uma abordagem mais comum para chamar o `QueryInterface` método na [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interface para a interface de enumerador apropriada e use métodos específicos do enumerador para acessar o conteúdo da tabela.  Consulte o [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md) interface para obter um exemplo.  
  
## Consulte também  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)