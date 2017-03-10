---
title: "CV_call_e | Microsoft Docs"
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
  - "Enumeração CV_call_e"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica a convenção de chamada para uma função.  
  
> [!NOTE]
>  Somente os valores de enumeração mais comuns estão documentados aqui.  A enumeração completa está disponível no arquivo de cabeçalho cvconst.h.  
  
## Sintaxe  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## Elements  
 CV\_CALL\_NEAR\_C  
 Especifica uma convenção de chamada de função usando um estudo curto de direita para a esquerda.  A função chamada limpa a pilha.  
  
 CV\_CALL\_NEAR\_FAST  
 Especifica uma convenção de chamada de função usando um próximo envio da esquerda para a direita com registradores.  A função chamada usa a soma dos bytes de parâmetro para limpar a pilha.  
  
 CV\_CALL\_NEAR\_STD  
 Especifica uma convenção de chamada de função usando uma chamada de padrão curto \(push da direita para a esquerda\).  
  
 CV\_CALL\_NEAR\_SYS  
 Especifica uma convenção de chamada de função usando uma chamada de sistema quase.  
  
 CV\_CALL\_THISCALL  
 Especifica uma convenção de chamada de função usando `this` de chamada \(`this` ponteiro passado no registro\).  
  
 CV\_CALL\_CLRCALL  
 Especifica uma convenção de chamada de função usada pelo CLR Common Language Runtime \(\) \(também conhecido como um código gerenciado convenção de chamada\).  
  
## Comentários  
 Os valores desta enumeração são retornados por uma chamada para o [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) método.  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)