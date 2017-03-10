---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
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
  - "Método IDiaSourceFile::get_checksumType"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera o tipo de soma de verificação.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna o tipo de soma de verificação.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 O tipo de soma de verificação é um valor que pode ser mapeado para um algoritmo de soma de verificação.  Por exemplo, o formato de arquivo PDB padrão normalmente pode ter um dos seguintes valores:  
  
|Tipo de soma de verificação|Rótulo de CryptoAPI|Descrição|  
|---------------------------------|-------------------------|---------------|  
|0|\<none\>.|Sem soma de verificação presente.|  
|1|`CALG_MD5`|a soma de verificação gerada com o algoritmo de hash MD5.|  
|2|`CALG_SHA1`|a soma de verificação gerada com o algoritmo de hash SHA1.|  
  
 O `CryptoAPI` rótulos são a partir de `ALG_ID` enumeração.  Para obter mais informações sobre algoritmos de hash, consulte o `CryptoAPI` seção do Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Para obter os bytes reais de soma de verificação para o arquivo de origem, chame o [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) método.  
  
## Consulte também  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)