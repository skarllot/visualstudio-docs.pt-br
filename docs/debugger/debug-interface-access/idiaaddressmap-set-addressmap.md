---
title: "IDiaAddressMap::set_addressMap | Microsoft Docs"
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
  - "Método IDiaAddressMap::set_addressMap"
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_addressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fornece um mapa do endereço para oferecer suporte a conversões de layout de imagem.  
  
## Sintaxe  
  
```cpp#  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### Parâmetros  
 `cbData`  
 \[in\] O número de elementos de `data` parâmetro.  
  
 `data[]`  
 \[in\] Uma matriz de [Estrutura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md) estruturas que definem o mapa de tradução.  
  
 `imagetoSymbols`  
 \[in\] `TRUE` se a `data` parâmetro define um mapa do novo layout de uma imagem ao layout original \(conforme descrito pelos símbolos de depuração\).  `FALSE`Se `data` é um mapa para o novo layout de imagem retirado do layout original.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Normalmente, o DIA recupera mapas de tradução de endereço do arquivo de banco de dados \(. PDB\) de programa.  Se esses valores estiverem faltando, o [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) método é chamado duas vezes, uma vez com o `imagetoSymbols` parâmetro definido como `TRUE` e uma vez com o `imagetoSymbols` parâmetro definido como `FALSE`.  Conversões de mapa de endereços não podem ser ativadas usando o [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md) método, a menos que os dois mapas de tradução são fornecidos.  
  
## Consulte também  
 [Estrutura DiaAddressMapEntry](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../Topic/IDiaAddressMap::put_addressMapEnabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)