---
title: "StackFrameTypeEnum | Microsoft Docs"
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
  - "Enumeração StackFrameTypeEnum"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Especifica o tipo de quadro de pilha.  
  
## Sintaxe  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Elements  
 `FrameTypeFPO`  
 Ponteiro do quadro não especificado; Info do FPO disponível.  
  
 `FrameTypeTrap`  
 Quadro de interceptação de kernel.  
  
 `FrameTypeTSS`  
 Quadro de interceptação de kernel.  
  
 `FrameTypeStandard`  
 Quadro de pilha EBP padrão.  
  
 `FrameTypeFrameData`  
 Ponteiro do quadro não especificado; Informações de dados de quadro disponíveis.  
  
 `FrameTypeUnknown`  
 Quadro que não tem qualquer informação de depuração.  
  
## Comentários  
 Os valores desta enumeração são retornados por uma chamada para o [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) método.  
  
## Requisitos  
 Cabeçalho: cvconst.h  
  
## Consulte também  
 [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)