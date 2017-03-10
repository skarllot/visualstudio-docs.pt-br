---
title: "A depura&#231;&#227;o de modo misto para processos IA64 n&#227;o &#233; compat&#237;vel. | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_ia64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# A depura&#231;&#227;o de modo misto para processos IA64 n&#227;o &#233; compat&#237;vel.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O Visual Studio não oferece suporte à depuração de modo misto de código gerenciado e nativo em processos IA64.  Isso significa que, durante a depuração, você não pode depurar de código gerenciado para código nativo e vice\-versa.  
  
### Soluções alternativas  
  
-   Depure seu código gerenciado e nativo em sessões separadas de depuração.  
  
     —ou—  
  
     Depure seu código misto como um processo de 32 bits, como descrito nos procedimentos a seguir.  
  
### Para alterar a plataforma para 32 bits \(Visual Basic ou C\#\)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades** no menu de atalho.  
  
2.  Nas páginas de propriedades, clique na guia **Compilar** ou **Depurar**.  
  
3.  Clique em **Plataforma** e selecione x86 na lista de plataformas.  
  
     Por padrão, os compiladores padrão do Visual Basic e do C\# produzem código para ser executado em qualquer CPU.  Em um computador de 64 bits, esses binários são executados como processos de 64 bits.  Para executar em um processo de 32 bits, você deve escolher **Win32** e não **AnyCPU**.  
  
### Para alterar a plataforma para 32 bits \(C\/C\+\+\)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades** no menu de atalho.  
  
2.  Nas Páginas de Propriedades, clique em **Plataforma** e selecione Win32 na lista de plataformas.  
  
## Consulte também  
 [Depurar aplicativos de 64 bits](../debugger/debug-64-bit-applications.md)