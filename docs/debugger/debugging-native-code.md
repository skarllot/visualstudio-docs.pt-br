---
title: "Depurando c&#243;digo nativo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depurando [C++], código nativo"
  - "depurando [Visual Studio], código nativo"
  - "depurando código nativo"
  - "código nativo, depuração"
ms.assetid: d94eee90-7e0d-4cac-88c1-9831030daa5e
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Depurando c&#243;digo nativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A seção aborda alguns problemas comuns de depuração e técnicas para aplicativos nativos.  As técnicas abordadas nesta seção são de alto nível.  Para conhecer a mecânica de usar o depurador do Visual Studio, consulte [Roteiro do depurador](../debugger/debugger-basics.md).  
  
## Nesta seção  
 [Como depurar o código otimizado](../debugger/how-to-debug-optimized-code.md)  
 Fornece dicas para depurar o código otimizado, especificamente, por que depurar uma versão não otimizada do programa, configurações padrão de otimização para configurações de Depuração e Versão, e dicas para localizar os bug que aparecem apenas no código otimizado \(ativação de otimização em uma configuração de compilação de Depuração\).  
  
 [DebugBreak e \_\_debugbreak](../debugger/debugbreak-and-debugbreak.md)  
 Descreve a função `DebugBreak` do Win32 e fornece um link para seu tópico de referência no SDK da plataforma.  Também descreve o `__debugbreak` intrínseco.  
  
 [Asserções C\/C\+\+](../debugger/c-cpp-assertions.md)  
 Discute instruções da asserção, como funcionam, os benefícios de usá\-las \(capturando erros lógicos, verificando resultados de uma operação e testando condições de erro\), sua interação com `_DEBUG` e os tipos de asserções com suporte no [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 [Como depurar código de assembly embutido](../debugger/how-to-debug-inline-assembly-code.md)  
 Fornece instruções curtas sobre como usar a janela Desmontagem para exibir as instruções de assembly e a janela Registros para exibir o conteúdo do registro e fornecer links para tópicos em relação a essas janelas.  
  
 [Técnicas de depuração MFC](../debugger/mfc-debugging-techniques.md)  
 Links para técnicas de depuração para programas MFC, incluindo: afxDebugBreak, a macro TRACE, detecção de vazamentos de memória no MFC, asserções do MFC e redução do tamanho de compilações de depuração do MFC.  
  
 [Técnicas de depuração CRT](../debugger/crt-debugging-techniques.md)  
 Links para técnicas de depuração para a biblioteca em tempo de execução C, incluindo o uso da biblioteca de depuração do CRT, macros para relatório, diferenças entre malloc e \_malloc\_dbg, escrevendo funções de gancho de depuração, e o heap de depuração do CRT.  
  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)  
 Fornece respostas a perguntas frequentes sobre depuração de programas do Visual C\+\+  
  
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)  
 Fornece informações sobre como depurar aplicativos COM e ActiveX, inclusive ferramentas que você pode usar para depuração de COM e ActiveX.  
  
 [Como depurar DLLs nativas](../Topic/How%20to:%20Debug%20Native%20DLLs.md)  
 Explica como configurar a depuração para DLLs de código nativo.  
  
 [Como depurar código injetado](../Topic/How%20to:%20Debug%20Injected%20Code.md)  
 Fornece orientação sobre o código de depuração que usa atributos.  As instruções incluem como ativar a Anotação de Origem, como exibir o código injetado e como exibir o código de desmontagem no ponto de execução atual.  
  
 [Instruções passo a passo: depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Descreve como usar as janelas de ferramentas de **Tarefas Paralelas** e **Pilhas Paralelas** para depurar um aplicativo paralelo.  
  
## Seções relacionadas  
 [Tipos de projeto do Visual C\+\+](../debugger/debugging-preparation-visual-cpp-project-types.md)  
 Fornece links para tópicos que descrevem como depurar os tipos de projeto nativos criados pelos modelos de projeto do Visual C\+\+.  
  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)  
 Fornece links para as maiores seções de documentação de depuração.  A informação inclui: novidades no depurador, configurações e preparação, pontos de interrupção, tratamentos de exceção, edição e continuação, depuração de código gerenciado, depuração de código nativo, depuração de SQL e referências à interface do usuário.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)