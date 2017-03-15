---
title: "IDiaEnumSectionContribs::Clone | Microsoft Docs"
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
  - "Método IDiaEnumSectionContribs::Clone"
ms.assetid: 81d3f3a7-3684-4e5c-b028-29b268684a2c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSectionContribs::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cria um enumerador que contém o mesmo estado de enumeração que o enumerador atual.  
  
## Sintaxe  
  
```cpp#  
HRESULT Clone(   
   IDiaEnumSectionContrib** ppenum  
);  
```  
  
#### Parâmetros  
 ppenum  
 \[out\] Retorna um [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md) objeto que contém uma duplicata do enumerador.  A seção de contribuições não são duplicados, apenas o enumerador.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)