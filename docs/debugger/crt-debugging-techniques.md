---
title: "T&#233;cnicas de depura&#231;&#227;o CRT | Microsoft Docs"
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
  - "c.runtime.debugging"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "CRT, depuração"
  - "depurando [C++], Suporte à depuração CRT"
  - "depuração [CRT]"
ms.assetid: 9be561f6-14a8-44ff-925d-d911d5b8e6ff
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# T&#233;cnicas de depura&#231;&#227;o CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se você estiver depurando um programa que usa a biblioteca em tempo de execução C, essas técnicas de depuração poderão ser úteis.  
  
## Nesta seção  
 [Uso da biblioteca de depuração CRT](../debugger/crt-debug-library-use.md)  
 Descreve o suporte à depuração fornecido pela biblioteca em tempo de execução C e fornece instruções para acessar as ferramentas.  
  
 [Macros para relatórios](../debugger/macros-for-reporting.md)  
 Fornece informações sobre as macros **\_RPTn** e **\_RPTFn** \(definidas em CRTDBG.H\), que substituem o uso de instruções `printf` para depuração.  
  
 [Versões de depuração das funções de alocação da pilha](../debugger/debug-versions-of-heap-allocation-functions.md)  
 Discute as versões especiais de depuração das funções de alocação de heap, incluindo: como o CRT mapeia as chamadas, os benefícios de chamá\-las explicitamente, como evitar a conversão, rastrear os tipos separados de alocações em blocos do cliente e os resultados de não definir \_DEBUG.  
  
 [Detalhes da pilha de depuração CRT](../debugger/crt-debug-heap-details.md)  
 Fornece links para o gerenciamento de memória e o heap de depuração, tipos de blocos no heap de depuração, como usar o heap de depuração, o estado de heap que informa funções e como controlar solicitações de alocação do heap.  
  
 [Gravação da função de gancho de depuração](../debugger/debug-hook-function-writing.md)  
 Lista links para funções de gancho de bloco de cliente, funções de gancho de alocação, ganchos de alocação e alocações de memória CRT, e funções de gancho de relatório.  
  
 [Localizando perdas de memória usando a biblioteca CRT](../debugger/finding-memory-leaks-using-the-crt-library.md)  
 Aborda técnicas para detectar e isolar vazamentos de memória usando o depurador e a biblioteca em tempo de execução C.  
  
## Seções relacionadas  
 [Depurando código nativo](../debugger/debugging-native-code.md)  
 Discute alguns problemas comuns e técnicas de depuração para aplicativos C e C\+\+.  
  
 [Segurança do depurador](../debugger/debugger-security.md)  
 Fornece recomendações para depuração mais segura.