---
title: "Passo a passo: Usando o depurador com m&#233;todos ass&#237;ncronos | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "recurso assíncrono, usando o depurador"
  - "Operador await, usando o depurador"
  - "Comando Step Into, no Operador await"
  - "Comando Step Out, dentro do método assíncrono"
  - "Comando Step Over, no Operador await"
ms.assetid: 5adb2531-3f09-4b7e-8baa-29de80abee6e
caps.latest.revision: 23
caps.handback.revision: 23
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
---
# Passo a passo: Usando o depurador com m&#233;todos ass&#237;ncronos
Usando o recurso Async, você pode chamar os métodos assíncronos sem usar retornos de chamada ou dividir seu código em vários métodos ou expressões lambda.  Para tornar síncrono um código assíncrono, chame um método assíncrono em vez de um método síncrono e adicione algumas palavras\-chave ao código.  Para obter mais informações, consulte [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 No depurador do Visual Studio, você pode usar os comandos **Depuração Completa**, **Depuração Parcial** e **Depuração Circular** com o recurso `Async`.  Você também pode continuar a usar pontos de interrupção, particularmente para exibir o fluxo de controle em uma instrução que contém um operador de espera.  Neste passo a passo, você executará as seguintes tarefas, que pode executar em qualquer ordem.  
  
-   Demonstrar o fluxo de controle em uma instrução de espera usando pontos de interrupção.  
  
-   Compreender o comportamento dos comandos **Depuração Completa** e **Depuração Parcial** em instruções que contêm um operador de espera.  
  
-   Compreender o comportamento do comando **Depuração Circular** quando você o usa a partir de um método assíncrono.  
  
## Pontos de interrupção para mostrar o fluxo de controle  
 Ao marcar um método com o modificador [Async](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) ou [async](/dotnet/csharp/language-reference/keywords/async) \(C\#\), você pode usar o operador [Await](/dotnet/visual-basic/language-reference/modifiers/async) \(Visual Basic\) ou [away](/dotnet/csharp/language-reference/keywords/await) \(C\#\) no método.  Para criar uma expressão de espera, associe o operador de espera a uma tarefa.  Quando uma expressão de espera é chamada para a tarefa, o método atual sai imediatamente e retorna uma tarefa diferente.  Quando a tarefa que está associada ao operador de espera for concluída, a execução retomará no mesmo método.  Para obter mais informações, consulte [Fluxo de controle em programas assíncronos](../Topic/Control%20Flow%20in%20Async%20Programs%20\(C%23%20and%20Visual%20Basic\).md).  
  
> [!NOTE]
>  Um método assíncrono retorna para o chamador quando encontra o primeiro objeto esperado que ainda não está completo ou atinge o final do método assíncrono, o que ocorrer primeiro.  
  
> [!NOTE]
>  Os aplicativos do console nestes exemplos usam o método <xref:System.Threading.Tasks.Task.Wait%2A> para impedir que o aplicativo termine em `Main`.  Você não deve usar o método <xref:System.Threading.Tasks.Task.Wait%2A> fora dos aplicativos do console porque pode ocorrer uma situação de deadlock.  
  
 O procedimento a seguir define pontos de interrupção para demonstrar o que acontece quando o aplicativo alcança uma instrução de espera.  Você também pode demonstrar o fluxo de controle adicionando instruções `Debug.WriteLine`.  
  
1.  Crie um aplicativo de console e cole o seguinte código nele:  
  
     [!code-cs[csAsyncDebugging#1](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_1.cs)]
     [!code-vb[csAsyncDebugging#1](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_1.vb)]  
  
2.  Definir pontos de interrupção de depuração nas três linhas que terminam com um comentário “definir ponto de interrupção”.  
  
3.  Escolha a tecla F5 ou escolha **Depurar**, **Iniciar Depuração** na barra de menus para executar o aplicativo.  
  
     O aplicativo vai para o método `ProcessAsync` e quebra na linha que contém o operador de espera.  
  
4.  Escolha a tecla F5 novamente.  
  
     Como o aplicativo parou em uma instrução que contém um operador de espera, o aplicativo imediatamente encerra o método assíncrono e retorna uma tarefa.  Portanto, o aplicativo encerra o método `ProcessAsync` e quebra no ponto de interrupção no método de chamada \(`Main`\).  
  
5.  Escolha a tecla F5 novamente.  
  
     Quando o método `DoSomethingAsync` for concluído, o código retomará após a instrução await no método de chamada.  Assim, o aplicativo quebra no ponto de interrupção no método `ProcessAsync`.  
  
     Quando `DoSomethingAsync` era esperado inicialmente, o método `ProcessAsync` foi encerrado e retornou uma tarefa.  Quando o método esperado `DoSomethingAsync` foi concluído, a avaliação de instrução de espera gerou o valor de retorno de `DoSomethingAsync`.  O método `DoSomethingAsync` é definido para retornar um `Task (Of Integer)` no Visual Basic ou `Task<int>` no C\#, portanto, o valor na instrução de retorno é um inteiro.  Para obter mais informações, consulte [Tipos de retorno assíncronos](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md).  
  
### Obtendo e em seguida aguardando uma tarefa  
 No método `ProcessAsync`, a instrução `Dim result = Await DoSomethingAsync()` \(Visual Basic\) ou `var result = await DoSomethingAsync();` \(C\#\) é uma contração das duas instruções a seguir:  
  
 [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
 [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
 A primeira linha de código chama o método assíncrono e retorna uma tarefa.  Essa tarefa é associada com o operador de espera na próxima linha de código.  A instrução de espera sai do método \(`ProcessAsync`\) e retorna uma tarefa diferente.  Quando a tarefa que está associada ao operador de espera for concluída, a execução retomará no mesmo método \(`ProcessAsync`\) depois da instrução de espera.  
  
 Quando a instrução de espera retorna imediatamente uma tarefa diferente, essa tarefa é o argumento retornado do método assíncrono que contém o operador de espera \(`ProcessAsync`\).  A tarefa que é retornada pela espera inclui a execução do código que ocorre depois da espera no mesmo método, por isso essa tarefa é diferente da tarefa associada com a espera.  
  
## Depuração Completa e Depuração Parcial  
 O comando **Depuração Completa** entra em um método, mas o comando **Depuração Parcial** executa a chamada do método e quebra na linha seguinte do método de chamada.  Para obter mais informações, consulte [Entrar ou sair do código](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Step_into__over__or_out_of_the_code).  
  
 O exemplo a seguir mostra o que ocorre quando você escolhe os comandos **Depuração Completa** ou **Depuração Parcial** em uma instrução de espera.  
  
1.  Substitua o código no aplicativo de console pelo código a seguir.  
  
     [!code-cs[csAsyncDebugging#3](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_3.cs)]
     [!code-vb[csAsyncDebugging#3](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_3.vb)]  
  
2.  Escolha a tecla F11 ou escolha **Depurar**, **Depuração Completa** na barra de menus para iniciar uma demonstração de comando `Step Into` em uma instrução que contém um operador de espera.  
  
     O aplicativo é iniciado e quebra na primeira linha, que é `Sub Main()` no Visual Basic ou na chave de abertura do método `Main` no C\#.  
  
3.  Escolha a tecla F11 mais três vezes.  
  
     O aplicativo agora deve estar na instrução de espera no método `ProcessAsync`.  
  
4.  Escolha a tecla F11.  
  
     O aplicativo vai no método `DoSomethingAsync` e quebra na primeira linha.  Esse comportamento ocorre mesmo que, na instrução `await`, o aplicativo retorne imediatamente para o método de chamada \(`Main`\).  
  
5.  Continue pressionando a tecla F11 até que o aplicativo retorne para a instrução de espera no método `ProcessAsync`.  
  
6.  Escolha a tecla F11.  
  
     O aplicativo quebra na linha seguinte à instrução de espera.  
  
7.  Na barra de menus, escolha **Depurar**, **Parar Depuração** para interromper a execução do aplicativo.  
  
     As etapas a seguir demonstram o comando **Depuração Parcial** em uma instrução de espera.  
  
8.  Escolha a tecla F11 quatro vezes ou escolha **Depurar**, **Depuração Completa** na barra de menus quatro vezes.  
  
     O aplicativo agora deve estar na instrução de espera no método `ProcessAsync`.  
  
9. Escolha a tecla F10 ou escolha **Depurar**, **Depuração Parcial** na barra de menus.  
  
     A execução quebra na linha seguinte à instrução de espera.  Esse comportamento ocorre mesmo que o aplicativo retorne imediatamente para o método de chamada \(`Main`\) na instrução de espera.  O comando `Step Over` também considera a execução do método `DoSomethingAsync`, como esperado.  
  
10. Na barra de menus, escolha **Depurar**, **Parar Depuração** para interromper a execução do aplicativo.  
  
     Como as etapas a seguir mostram, o comportamento dos comandos **Depuração Completa** e **Depuração Parcial** diferem ligeiramente quando o operador de espera está em uma linha diferente da chamada para o método assíncrono.  
  
11. No método `ProcessAsync`, substitua a instrução de espera pelo seguinte código.  A instrução de espera original é uma contração das duas instruções a seguir.  
  
     [!code-cs[csAsyncDebugging#2](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_2.cs)]
     [!code-vb[csAsyncDebugging#2](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_2.vb)]  
  
12. Escolha a tecla F11 ou escolha **Depurar**, **Depuração Completa** na barra de menus várias vezes para iniciar a execução e percorrer o código.  
  
     Na chamada para `DoSomethingAsync`, o comando **Depuração Completa** quebra no método `DoSomethingAsync`, enquanto o comando **Depuração Parcial** vai para a próxima instrução, como esperado.  Na instrução de espera, ambos os comandos quebram na instrução que segue a espera.  
  
## Depuração Circular  
 Nos métodos que não são assíncronos, o comando **Depuração Circular** quebra no método de chamada no código que segue a chamada do método.  Para métodos assíncronos, a lógica para onde a execução quebra no método de chamada é mais complexa, e essa lógica depende se o comando **Depuração Circular** está na primeira linha do método assíncrono.  
  
1.  Substitua o código no aplicativo de console pelo código a seguir.  
  
     [!code-cs[csAsyncDebugging#4](../misc/codesnippet/CSharp/walkthrough-using-the-debugger-with-async-methods_4.cs)]
     [!code-vb[csAsyncDebugging#4](../misc/codesnippet/VisualBasic/walkthrough-using-the-debugger-with-async-methods_4.vb)]  
  
2.  Definir um ponto de interrupção na linha de `Debug.WriteLine("before")` no método `DoSomethingAsync`.  
  
     Isso é para demonstrar o comportamento do comando **Depuração Circular** de uma linha em um método assíncrono que não é a primeira linha.  
  
3.  Escolha a tecla F5 ou escolha **Depurar**, **Iniciar Depuração** na barra de menus para iniciar o aplicativo.  
  
     O código quebra em `Debug.WriteLine("before")` no método `DoSomethingAsync`.  
  
4.  Escolha as teclas Shift \+ F11 ou escolha **Depurar**, **Depuração Circular** na barra de menus.  
  
     O aplicativo quebra no método de chamada na instrução de espera para a tarefa associada ao método atual.  Como resultado, o aplicativo quebra na instrução de espera no método `ProcessAsync`.  O aplicativo não quebra em `Dim z = 0` \(no Visual Basic\) ou em `int z = 0;` \(C\#\), que é o código que segue a chamada para o método `DoSomethingAsync`.  
  
5.  Escolha **Depurar**, **Parar Depuração** na barra de menus para interromper a execução do aplicativo.  
  
     As etapas a seguir demonstram o que acontece quando você usa o comando **Depuração Circular** da primeira linha de um método assíncrono.  
  
6.  Remova o ponto de interrupção existente e adicione um ponto de interrupção na primeira linha do método `DoSomethingAsync`.  
  
     No C\#, adicione o ponto de interrupção na chave de abertura do método `DoSomethingAsync`.  No Visual Basic, adicione o ponto de interrupção na linha que contém `Async Function DoSomethingAsync() As Task(Of Integer)`.  
  
7.  Escolha a tecla F5 para iniciar o aplicativo.  
  
     O código quebra na primeira linha do método `DoSomethingAsync`.  
  
8.  Na barra de menus, escolha **Depurar**, **Janelas**, **Saída**.  
  
     A janela **Saída** é aberta.  
  
9. Escolha as teclas Shift \+ F11 ou escolha **Depurar**, **Depuração Circular** na barra de menus.  
  
     O aplicativo é retomado até que o método assíncrono alcance sua primeira espera, e o aplicativo quebra na instrução de chamada.  Como resultado, o aplicativo quebra em `Dim the Task = DoSomethingAsync()` \(Visual Basic\) ou em `var theTask = DoSomethingAsync();` \(C\#\).  A mensagem “antes” apareceu na janela de saída, mas a mensagem “depois” ainda não.  
  
10. Escolha a tecla F5 para continuar a executar o aplicativo.  
  
     O aplicativo continua com a instrução que segue a instrução de espera na função assíncrona chamada \(`DoSomethingAsync`\).  A mensagem “depois” aparece na janela de saída.  
  
## Consulte também  
 [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)