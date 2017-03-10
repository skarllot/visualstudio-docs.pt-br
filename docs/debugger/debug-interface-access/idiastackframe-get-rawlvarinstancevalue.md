---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
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
  - "Método IDiaStackFrame::get_rawLVarInstanceValue"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este método recupera o valor da variável local especificado como bytes brutos.  
  
## Sintaxe  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### Parâmetros  
 `pInstance`  
 \[in\] Um `IDiaLVarInstance` representando uma instância de variável local para obter o valor do objeto.  
  
 `cbDataMax`  
 \[in\] Número máximo de bytes no buffer apontada por `pbData`.  Isso pode ter no máximo de 8 bytes \(`sizeof(ULONGLONG)`\).  
  
 `pcbData`  
 \[out\] Retorna o número real de bytes armazenados no buffer.  
  
 `pbData`  
 \[out\] Um buffer para ser preenchido com dados.  Isso não pode ser `NULL`.  
  
## Valor de retorno  
 Se bem\-sucedida, retorna `S_OK`; Caso contrário, retorna um código de erro.  
  
## Consulte também  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)