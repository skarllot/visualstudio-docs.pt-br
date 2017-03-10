---
title: "Instru&#231;&#245;es passo a passo: depurando na hora de design | Microsoft Docs"
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
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "pontos de interrupção, depuração no tempo de design"
  - "depurando [Visual Studio], tempo de design"
  - "depuração no tempo de design"
  - "Janela Imediata, depuração no tempo de design"
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Instru&#231;&#245;es passo a passo: depurando na hora de design
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode usar a janela **Imediato** do Visual Studio para executar uma função ou sub\-rotina enquanto seu aplicativo não estiver em execução.  Se a função ou a sub\-rotina contiverem um ponto de interrupção, o Visual Studio interromperá a execução no ponto apropriado.  Então, você poderá usar o depurador do Windows para examinar o estado do programa.  Esse recurso é chamado de depuração em tempo de design.  
  
 O procedimento a seguir exibe como usar esse recurso.  
  
### Para usar pontos de interrupção da janela Imediato  
  
1.  Cole o seguinte código no aplicativo de console do Visual Basic:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Defina um ponto de interrupção na linha em que se lê `s="Add BreakPoint Here"`.  
  
3.  Digite o seguinte na janela **Imediato**: `?MyFunction<enter>`  
  
4.  Certifique\-se de que o ponto de interrupção foi alcançado, e que a pilha de chamadas está correta.  
  
5.  No menu **Depurar**, clique em **Continuar** e verifique se você ainda está no modo de design.  
  
6.  Digite o seguinte na janela **Imediato**: `?MyFunction<enter>`  
  
7.  Digite o seguinte na janela **Imediato**: `?MySub<enter>`  
  
8.  Verifique se você alcançou o ponto de interrupção e examine o valor da variável estática `i` na janela **Locais**.  Deve ter o valor 3.  
  
9. Verifique se a pilha de chamadas está correta.  
  
10. No menu **Depurar**, clique em **Continuar** e verifique se você ainda está no modo de design.  
  
## Consulte também  
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Noções básicas do depurador](../debugger/debugger-basics.md)