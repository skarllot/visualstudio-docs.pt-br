---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera correspondente a seqüência de nomes para dada identificadores de propriedade.  
  
## Sintaxe  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### Parâmetros  
 `cpropid`  
 \[in\] Número de identificações de propriedade em `rgpropid`.  
  
 `rgpropid`  
 \[in\] Matriz de ids de propriedade para o qual deseja obter os nomes \(`PROPID` é definido em WTypes.h como um `ULONG`\).  
  
 `rglpwstrName`  
 \[in, out\] Matriz de nomes de propriedades para as identificações de propriedade especificada.  A matriz deve ser pré\-alocado para conter o número solicitado de nomes de propriedade e deve ser capaz de armazenar ao menos `cpropid``BSTR` seqüências de caracteres.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Os nomes de propriedade retornado devem ser liberados \(chamando o `SysFreeString` função\) quando eles não são mais necessários.  
  
## Consulte também  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)