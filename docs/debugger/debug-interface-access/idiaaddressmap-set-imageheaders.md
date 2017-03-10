---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
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
  - "Método IDiaAddressMap::set_imageHeaders"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Conjuntos de cabeçalhos para habilitar a tradução de endereço virtual relativo de imagem.  
  
## Sintaxe  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### Parâmetros  
 cbData diferente  
 \[in\] Número de bytes de dados de cabeçalho.  Deve ser `n*sizeof(IMAGE_SECTION_HEADER)` onde `n` é o número de cabeçalhos de seção no executável.  
  
 Data\]  
 \[in\] Uma matriz de `IMAGE_SECTION_HEADER` estruturas para serem usados como os cabeçalhos de imagem.  
  
 originalHeaders  
 \[in\] Definido como `FALSE` se os cabeçalhos de imagem são da nova imagem, `TRUE` se eles refletem a imagem original antes de uma atualização.  Normalmente, isso seria definido como `TRUE` somente em combinação com chamadas para o [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 O `IMAGE_SECTION_HEADER` estrutura é declarada em Winnt. h e representa o formato de cabeçalho de seção de imagem do executável.  
  
 Cálculos de endereço virtual relativo dependem do `IMAGE_SECTION_HEADER` valores.  Normalmente, o DIA recupera esses desde o arquivo de banco de dados \(. PDB\) do programa.  Se esses valores estiverem faltando, o DIA é não é possível calcular endereços virtuais relativos e o [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md) método retorna `FALSE`.  Em seguida, em que o cliente deve chamar o [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md) método para ativar os cálculos de endereço virtual relativo depois de fornecer os cabeçalhos de imagem ausente da própria imagem.  
  
## Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)