---
title: "A depura&#231;&#227;o de modo misto s&#243; &#233; suportada quando o Microsoft .NET Framework 2.0 ou 3.0 &#233; usado | Microsoft Docs"
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
  - "vs.debug.error.interop_unsupported_to_old"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# A depura&#231;&#227;o de modo misto s&#243; &#233; suportada quando o Microsoft .NET Framework 2.0 ou 3.0 &#233; usado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

As versões do Microsoft .NET Framework anteriores à versão 2.0 não fornecem suporte à depuração de modo misto de processos de 64 bits.  Isso significa que, durante a depuração, você não pode depurar de código gerenciado para código nativo e vice\-versa.  
  
 Para resolver esse problema, você pode:  
  
-   Atualize seu projeto para usar o Microsoft .NET Framework 2.0 ou 3.0.  
  
-   Depure seu código gerenciado e nativo em sessões separadas de depuração.  
  
-   Depure seu código misto como um processo de 32 bits, como descrito nos procedimentos a seguir.  
  
### Para alterar o sistema operacional para 32 bits \(Visual Basic ou C\#\)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades** no menu de atalho.  
  
2.  Nas páginas de propriedades, clique na guia **Compilar** ou **Depurar**.  
  
3.  Clique em **Plataforma** e selecione **x86** na lista de plataformas.  
  
     Por padrão, os compiladores do Visual Basic e do C\# produzem código para ser executado em qualquer CPU.  Em um computador de 64 bits, esses binários são executados como processos de 64 bits.  Para executar em um processo de 32 bits, você deve escolher **Win32** e não **AnyCPU**.  
  
### Para alterar o sistema operacional para 32 bits \(C\/C\+\+\)  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto e clique em **Propriedades** no menu de atalho.  
  
     Nas Páginas de Propriedades, clique em **Plataforma** e selecione **Win32** na lista de plataformas.  
  
### Para corrigir este erro  
  
-   Consulte [Setting Up SQL Debugging](http://msdn.microsoft.com/pt-br/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## Consulte também  
 [Depurar aplicativos de 64 bits](../debugger/debug-64-bit-applications.md)