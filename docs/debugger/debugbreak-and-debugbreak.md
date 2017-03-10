---
title: "DebugBreak e __debugbreak | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DebugBreak"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "pontos de interrupção, Função DebugBreak"
  - "Função DebugBreak"
  - "depurando [C++], Função DebugBreak"
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DebugBreak e __debugbreak
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode chamar a função DebugBreak do Win32 ou a [\_\_debugbreak](/visual-cpp/intrinsics/debugbreak) intrínseca em qualquer ponto em seu código.  `DebugBreak` e `__debugbreak` têm o mesmo efeito de definir um ponto de interrupção nesse local.  
  
 Como `DebugBreak` é uma chamada para uma função do sistema, os símbolos de depuração do sistema devem ser instalados para garantir que as informações corretas da pilha de chamadas sejam exibidas depois de interromper.  Caso contrário, as informações da pilha de chamadas exibidas pelo depurador podem estar desativadas por um quadro.  Se você usar `__debugbreak`, os símbolos não serão necessários.  
  
## Consulte também  
 [Intrínsecos do compilador](/visual-cpp/intrinsics/compiler-intrinsics)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando código nativo](../debugger/debugging-native-code.md)   
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)