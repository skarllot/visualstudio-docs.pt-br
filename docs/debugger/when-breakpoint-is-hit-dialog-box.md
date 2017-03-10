---
title: "Caixa de di&#225;logo Ponto de Interrup&#231;&#227;o Quando Visitado | Microsoft Docs"
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
  - "vs.debug.whenbreakpointishit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Ponto de Interrup&#231;&#227;o Quando Visitado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Com essa caixa de diálogo, você pode personalizar a ação que ocorre quando um ponto de interrupção é atingido.  
  
## Lista UIElement  
 **Imprimir uma mensagem**  
 Imprime uma mensagem, usando a sintaxe do DebuggerDisplay.  Para obter mais informações, consulte [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md).  
  
 Essa caixa de texto também oferece suporte à palavras\-chave especiais \(como $ADDRESS\) que podem ser usadas por si mesmas ou nas chaves de uma expressão do DebuggerDisplay.  As palavras\-chave disponíveis são listadas na caixa de diálogo.  
  
 **Continuar a execução**  
 Esse controle só será habilitado quando **Imprimir uma mensagem** for selecionado.  Com esse controle selecionado, você pode usar um ponto de interrupção como um tracepoint para rastrear a execução do programa, em vez de interrompê\-lo quando o local for atingido.  
  
## Consulte também  
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)   
 [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)