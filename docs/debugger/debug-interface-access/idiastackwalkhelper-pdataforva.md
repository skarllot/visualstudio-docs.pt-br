---
title: "IDiaStackWalkHelper::pdataForVA | Microsoft Docs"
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
  - "Método IDiaStackWalkHelper2::pdataByVA"
ms.assetid: fafc38fe-74dc-4726-9a51-eebf3a673d7f
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::pdataForVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Retorna o bloco de dados PDATA associado ao endereço virtual.  
  
## Sintaxe  
  
```cpp#  
HRESULT pdataForVA(   
   ULONGLONG  va,  
   DWORD      cbData,  
   DWORD*     pcbData,  
   BYTE*      pbData  
);  
```  
  
#### Parâmetros  
 `va`  
 \[in\] Especifica o endereço virtual para obter dados.  
  
 `cbData`  
 \[in\] O tamanho dos dados em bytes para obter.  
  
 `pcbData`  
 \[out\] Retorna o tamanho real dos dados em bytes que foram obtidas.  
  
 `pbData`  
 \[in, out\] Um buffer que é preenchido com os dados solicitados.  Não pode ser `NULL`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`.  Retorna `S_FALSE` se não houver nenhum PDATA para o endereço especificado.  Caso contrário, retorna um código de erro.  
  
## Comentários  
 O PDATA \(a seção denominada ".pdata"\) de um compiland contém informações sobre funções de manipulação de exceção.  
  
 O chamador sabe a quantidade de dados deve ser retornado para que o chamador tenha nem precisa perguntar para a quantidade de dados está disponível.  Portanto, é aceitável para uma implementação desse método para retornar um erro se o `pbData` parâmetro é `NULL`.  
  
## Consulte também  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)