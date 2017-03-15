---
title: "Como posso descobrir quem est&#225; passando um valor de par&#226;metro incorreto? | Microsoft Docs"
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
  - "vs.debug.parameters"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "depurando [C++], parâmetros"
  - "funções [depurador], detectando valores de parâmetro incorretos"
  - "valores de parâmetros, solucionando problemas"
  - "parâmetros [depurador]"
  - "passando parâmetros, solucionando problemas de valores incorretos"
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como posso descobrir quem est&#225; passando um valor de par&#226;metro incorreto?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrição do problema  
 O valor de parâmetro errado está sendo passado a uma de minhas funções.  Essa função é chamada de todos os pontos  Como posso descobrir o que está passando o valor errado?  
  
## Solução  
  
#### Para resolver esse problema  
  
1.  Defina um local de ponto de interrupção no início da função.  
  
2.  Clique com o botão direito do mouse no ponto de interrupção e selecione **Condição**.  
  
3.  Na caixa de diálogo **Condição de Ponto de Interrupção**, clique na caixa de seleção **Condição**.  Consulte [Pontos de interrupção avançados](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Digite uma expressão, como `Var==3`, na caixa de texto, onde `Var` é o nome do parâmetro que contém o valor incorreto, e `3` é o valor incorreto passado para ele.  
  
5.  Selecione o botão de opção **é Verdadeiro** e clique no botão **OK**.  
  
6.  Agora, execute o programa novamente.  O ponto de interrupção faz com que o programa pare no início da função quando o parâmetro `Var` tiver o valor `3`.  
  
7.  Use a janela Pilha de Chamadas para localizar a função de chamada e navegar até seu código\-fonte.  Para obter mais informações, consulte [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
## Consulte também  
 [Perguntas frequentes de depuração do código nativo](../debugger/debugging-native-code-faqs.md)   
 [Breakpoints](http://msdn.microsoft.com/pt-br/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Depurando código nativo](../debugger/debugging-native-code.md)