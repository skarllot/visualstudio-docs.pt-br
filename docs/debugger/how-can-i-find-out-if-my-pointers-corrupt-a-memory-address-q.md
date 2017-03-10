---
title: "Como posso saber se meus ponteiros corrompem um endere&#231;o de mem&#243;ria? | Microsoft Docs"
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
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "endereços, ponteiros que corrompem endereços de memória"
  - "endereços de memória corrompidos"
  - "depurando [C++], corrompimento de memória"
  - "corrompimento de endereços de memória causado por ponteiros"
  - "memória, corrompimento"
  - "ponteiros, corrompendo endereços de memória"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como posso saber se meus ponteiros corrompem um endere&#231;o de mem&#243;ria?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrição do problema  
 Eu acho que um de meus ponteiros pode estar danificando a memória no endereço 0x00408000.  Como posso descobrir o que está acontecendo lá?  
  
## Solução  
  
#### Verificação de danos do heap  
  
-   A maior parte das corrupções de memória acontece, na verdade, devido à corrupção da heap.  Tente usar o utilitário global dos sinalizadores \(gflags.exe\) ou pageheap.exe.  Consulte [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### Para localizar onde o endereço de memória foi alterado  
  
1.  Defina um ponto de interrupção de dados em 0x00408000.  See [Definir um ponto de interrupção de alteração de dados \(somente C\+\+ nativo\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_).  
  
2.  Quando você atingir o ponto de interrupção, use a janela **Memória** para exibir o conteúdo da memória que começam em 0x00408000.  Para obter mais informações, consulte [Janelas de memória](../debugger/memory-windows.md).  
  
## Consulte também  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)