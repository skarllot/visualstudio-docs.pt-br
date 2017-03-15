---
title: "IDiaSymbol::get_container | Microsoft Docs"
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
  - "Método IDiaSymbol::get_container"
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta função recupera um ponteiro para um símbolo que representa o recipiente pai\/deste símbolo.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna um ponteiro para um `IDiaSymbol` que contém informações sobre o recipiente deste símbolo.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna S\_OK; Caso contrário, retornará S\_FALSE ou um código de erro.  
  
> [!NOTE]
>  Um valor de retorno de S\_FALSE significa que a propriedade não está disponível para o símbolo.  
  
## Requisitos  
  
|Requisito|Descrição|  
|---------------|---------------|  
|Cabeçalho:|dia2.h|  
|Versão:|V 8.0 do SDK DIA|  
  
## Consulte também  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)