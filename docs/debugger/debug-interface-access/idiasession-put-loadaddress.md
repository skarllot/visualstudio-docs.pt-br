---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
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
  - "Método IDiaSession::put_loadAddress"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Define o endereço de carga para o arquivo executável que corresponde aos símbolos desse armazenamento de símbolo.  
  
## Sintaxe  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### Parâmetros  
 `NewVal`  
 \[in\] Carregar o endereço para o arquivo executável.  
  
## Comentários  
 Propriedades do símbolo endereço virtual \(VA\) são calculadas usando o valor desse método.  Endereços virtuais não são calculados, a menos que essa propriedade é definida como diferente de zero.  
  
> [!NOTE]
>  Você deve chamar esse método quando você chega a [IDiaSession](../../debugger/debug-interface-access/idiasession.md) object e antes de começar a usar o objeto, se você precisar usar quaisquer propriedades virtuais nos símbolos.  
  
## Consulte também  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)