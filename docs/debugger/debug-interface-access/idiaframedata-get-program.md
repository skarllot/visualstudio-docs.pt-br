---
title: "IDiaFrameData::get_program | Microsoft Docs"
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
  - "Método IDiaFrameData::get_program"
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera a seqüência do programa que é usada para calcular o registro definido antes da chamada para a função atual.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### Parâmetros  
 `pRetVal`  
 \[out\] Retorna a seqüência do programa.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não há suporte para esta propriedade.  Caso contrário, retorna um código de erro.  
  
## Comentários  
 A seqüência do programa é uma seqüência de macros que é interpretada para estabelecer o prólogo.  Por exemplo, um quadro de pilha típica pode usar a seqüência de caracteres do programa `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="`.  O formato é a notação reversa polonês, onde os operadores seguem os operandos.  `T0`representa uma variável temporária na pilha.  Este exemplo executa as seguintes etapas:  
  
1.  Move o conteúdo do registrador de `ebp` para `T0`.  
  
2.  Adicionar `4` com o valor em `T0` para produzir um endereço, obter o valor desse endereço e armazenar o valor no registro de `eip`.  
  
3.  Obter o valor do endereço armazenado em `T0` e armazene esse valor no registro de `ebp`.  
  
4.  Adicionar `8` com o valor em `T0` e armazene esse valor no registro de `esp`.  
  
 Observe que a seqüência de caracteres do programa é específica para a CPU e a convenção de chamada definido para a função representada por um quadro de pilha atual.  
  
## Consulte também  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)