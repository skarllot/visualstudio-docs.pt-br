---
title: "A depura&#231;&#227;o do modo misto para processos x64 s&#243; &#233; suportada durante o uso do Microsoft.NET Framework 4 ou superior | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# A depura&#231;&#227;o do modo misto para processos x64 s&#243; &#233; suportada durante o uso do Microsoft.NET Framework 4 ou superior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As versões do .NET Framework anteriores à versão 4 não fornecem suporte à depuração de modo misto de processos do x64.  Isso significa que você não pode depurar de código gerenciado para código nativo, ou do código nativo para o código gerenciado.  
  
### Soluções alternativas  
  
-   Atualize seu projeto para usar o Microsoft .NET Framework 4 ou posterior.  
  
     —ou—  
  
     Depure seu código gerenciado e nativo em sessões separadas de depuração.  
  
     —ou—  
  
     Depure seu código misto como um processo de 32 bits, como descrito nos procedimentos a seguir.  
  
### Para alterar a plataforma para 32 bits \(Visual Basic ou C\#\)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do seu projeto e clique em **Propriedades**.  
  
2.  Nas páginas de propriedades, clique na guia **Compilar** ou **Depurar**.  
  
3.  Clique em **Plataforma** e selecione x86 na lista de plataformas.  
  
     Por padrão, os compiladores padrão do Visual Basic e do C\# produzem código para ser executado em qualquer CPU.  Em um computador de 64 bits, esses binários são executados como processos de 64 bits.  Para executar em um processo de 32 bits, você deve escolher **Win32** e não **AnyCPU**.  
  
### Para alterar a plataforma para 32 bits \(C\/C\+\+\)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó do seu projeto e clique em **Propriedades**.  
  
2.  Nas Páginas de Propriedades, clique em **Plataforma** e selecione Win32 na lista de plataformas.  
  
### Para corrigir este erro  
  
-   Consulte [Setting Up SQL Debugging](http://msdn.microsoft.com/pt-br/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## Consulte também  
 [Depurar aplicativos de 64 bits](../debugger/debug-64-bit-applications.md)