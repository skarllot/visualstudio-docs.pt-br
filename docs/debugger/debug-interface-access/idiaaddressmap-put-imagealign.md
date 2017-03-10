---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "Método IDiaAddressMap::put_imageAlign"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Define o alinhamento da imagem.  
  
## Sintaxe  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### Parâmetros  
 NewVal  
 \[in\] O novo valor de alinhamento de imagem para o executável.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Imagens \(executáveis carregada\) são alinhadas em limites de memória especificado.  Esse alinhamento pode ser afetado pela arquitetura do sistema atual e opções de tempo de compilação e o link.  Alinhamento da imagem está sempre em limites de bytes.  Os valores de alinhamento de imagem a seguir são válidos: limites de 1, 2, 4, 8, 16, 32 e 64 bytes.  
  
 O alinhamento da imagem atual pode ser recuperado com uma chamada para o [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) método.  
  
> [!NOTE]
>  A imagem já está carregada no momento em que esse método pode ser chamado.  O `put_imageAlign` método é normalmente usado quando a imagem tenha sido movida ou alterada e um novo alinhamento é necessário.  
  
## Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)