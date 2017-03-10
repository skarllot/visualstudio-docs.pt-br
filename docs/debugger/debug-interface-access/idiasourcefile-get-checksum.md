---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "Método IDiaSourceFile::get_checksum"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera os bytes de soma de verificação.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parâmetros  
 `cbData`  
 \[in\] Tamanho do buffer de dados, em bytes.  
  
 `pcbData`  
 \[out\] Retorna o número de bytes de soma de verificação.  Este parâmetro não pode ser `NULL`.  
  
 `data`  
 \[in, out\] Um buffer que é preenchido com os bytes de soma de verificação.  Se este parâmetro for `NULL`, em seguida, `pcbData` retorna o número de bytes necessários.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Comentários  
 Para determinar o tipo de algoritmo de soma de verificação que foi usado para gerar os bytes de soma de verificação, chame o [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) método.  
  
 A soma de verificação normalmente é gerada a partir da imagem do arquivo de origem para que as alterações no arquivo de origem são refletidas em alterações nos bytes soma de verificação.  Se os bytes de soma de verificação não coincidem com uma soma de verificação gerada a partir de imagem carregada do arquivo, e em seguida, o arquivo deve ser considerado danificado ou violado.  
  
 As somas de verificação típicas nunca são mais de 32 bytes de tamanho, mas não assumem que é o tamanho máximo de uma soma de verificação.  Definir o `data` parâmetro para `NULL` para obter o número de bytes necessários para recuperar a soma de verificação.  Em seguida, alocar um buffer de tamanho apropriado e chamar esse método, mais uma vez com o novo buffer.  
  
## Consulte também  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)