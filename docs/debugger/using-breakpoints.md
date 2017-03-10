---
title: "Usando pontos de interrup&#231;&#227;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
f1_keywords: 
  - "vs.debug.breakpointswin"
  - "vs.debug.disassembly.insert"
  - "vs.debug.sourcewin.edit"
  - "vs.debug.file"
  - "vs.debug.breakpt.new"
  - "vs.debug.whenbreakpointishit"
  - "vs.debug.breakpt.choose"
  - "vs.debug.breakpt.location.address"
  - "vs.debug.breakpt.constraints"
  - "vs.debug.breakpoints.delete"
  - "vs.debug.breakpt.location.data"
  - "vc.breakpoints"
  - "vs.debug.breakpt.condition"
  - "vs.debug.breakpt.location.function"
  - "vs.debug.breakpoints"
  - "vs.debug.menu.insert"
  - "vs.debug.filenames"
  - "vs.debug.breakpt.action"
  - "vs.debug.sourcewin.insert"
  - "vs.debug.address"
  - "vs.debug.data"
  - "vs.debug.func"
  - "vs.debug.breakpt.location.file"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "pontos de interrupção, sobre pontos de interrupção"
ms.assetid: 020b2e97-3b3e-4b2c-872d-b5c6025e120e
caps.latest.revision: 57
caps.handback.revision: 56
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Usando pontos de interrup&#231;&#227;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Você pode definir pontos de interrupção quando você deseja interromper a execução do depurador, talvez para ver o estado de variáveis de código ou para examinar a pilha de chamadas. Eles são uma das técnicas de depuração mais importantes na caixa de ferramentas do desenvolvedor.  
  
##  <a name="BKMK_Overview"></a> Definindo um ponto de interrupção no código\-fonte  
 Você pode definir um ponto de interrupção no código\-fonte clicando na margem esquerda de um arquivo de código fonte ou colocando o cursor em uma linha de código e pressionando F9. O ponto de interrupção aparece como um ponto vermelho na margem esquerda e a linha de código é colorida assim:  
  
 ![Set a breakpoint](../debugger/media/basicbreakpoint.png "BasicBreakpoint")  
  
 Quando você executa este código no depurador, a execução pára sempre que o ponto de interrupção é atingido antes que o código nessa linha é executado. A linha de código\-fonte é colorida amarela:  
  
 ![Breakpoint execution stopped](../debugger/media/breakpointexecution.png "BreakpointExecution")  
  
 Neste ponto, o valor de `testInt` ainda é 1.  
  
 Você pode examinar o estado atual do aplicativo, incluindo os valores de variáveis e a pilha de chamadas. Para obter mais informações sobre a pilha de chamadas, consulte [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md).  
  
 Você pode definir um ponto de interrupção em qualquer linha de código executável. Por exemplo, no c\# o código acima, você pode definir um ponto de interrupção na declaração de variável, o `for` loop ou qualquer código dentro de `for` loop, mas você não pode definir um ponto de interrupção em declarações de namespace ou classe ou a assinatura do método.  
  
##  <a name="BKMK_Set_a_breakpoint_in_a_source_file"></a> Definir outros tipos de pontos de interrupção  
 Você também pode definir pontos de interrupção na pilha de chamadas, na janela de desmontagem e, em código C\+\+ nativo, em uma condição de dados ou um endereço de memória.  
  
## Definindo um ponto de interrupção na janela pilha de chamadas  
 Você pode interromper a execução na instrução ou na linha de uma função de chamada retorna, definindo um ponto de interrupção **pilha de chamadas** janela. Para obter mais informações sobre a pilha de chamadas, consulte [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md). O depurador deve ter parado de execução.  
  
1.  Iniciar a depuração do aplicativo e execução de espera é interrompida \(por exemplo, em um ponto de interrupção\). Abra o **pilha de chamadas** janela \(**Debug \/ Windows \/ pilha de chamadas**, ou **CTRL \+ ALT \+ C**\).  
  
2.  A função de chamada e, em seguida, selecione **ponto de interrupção \/ Inserir ponto de interrupção**, ou apenas usar a tecla de atalho **F9**.  
  
3.  Um símbolo de ponto de interrupção aparece na margem esquerda da pilha de chamadas, ao lado do nome da chamada de função.  
  
 No **pontos de interrupção** janela, o ponto de interrupção de pilha de chamada aparece como um endereço com um local da memória que corresponde a próxima instrução executável na função. O depurador interrompe a execução na instrução.  
  
 Visualmente rastreamento pontos de interrupção durante a execução de código, consulte [Mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
## Definindo um ponto de interrupção na janela de desmontagem  
 Para definir um ponto de interrupção em uma instrução de assembly, o depurador deve estar no modo de interrupção.  
  
1.  Iniciar a depuração do aplicativo e execução de espera é interrompida \(por exemplo, em um ponto de interrupção\). Abra o **desmontagem** janela \(**Debug \/ Windows \/ desmontagem**, ou **Ctrl \+ Alt \+ D**\).  
  
2.  Clique na margem esquerda na instrução que você deseja quebrar em ou definir o cursor na instrução e pressione **F9**.  
  
## Definindo um ponto de interrupção de dados \(somente C\+\+ nativo\)  
 Pontos de interrupção interromper a execução quando um valor que é armazenado em alterações de um endereço de memória especificado. Se o valor for lido mas não alterado, a execução não será interrompido. Para definir pontos de interrupção de dados, o depurador deve estar no modo de interrupção.  
  
1.  Inicie a depuração do aplicativo e aguardar até que um ponto de interrupção é atingido. No **Depurar** menu, escolha **novo ponto de interrupção \/ ponto de interrupção de dados** \(ou abrir o **pontos de interrupção** janela e escolha **novo \/ ponto de interrupção de dados**.  
  
2.  No **endereço** digite um endereço de memória ou uma expressão que é avaliada como um endereço de memória. Por exemplo, digite `&avar` para interromper quando o conteúdo da variável `avar` alterações.  
  
3.  No **contagem de bytes** lista suspensa, selecione o número de bytes que você deseja que o depurador assistir. Por exemplo, se você selecionar **4**, o depurador observará os quatro bytes começando em `&avar` e interromperá se quaisquer um dos bytes alterar o valor.  
  
 Tenha em mente que os pontos de interrupção de dados dependem da aplicabilidade de endereços específicos de memória.  
  
-   Altera o endereço de uma variável de uma sessão de depuração para o próximo. Pontos de interrupção de dados serão desabilitados automaticamente no final de cada sessão de depuração.  
  
-   Se você definir um ponto de interrupção de dados em uma variável local, o permanece de ponto de interrupção habilitado quando a função termina, mas o endereço de memória não é mais aplicável, e o comportamento do ponto de interrupção é imprevisível. Se você definir um ponto de interrupção de dados em uma variável local, você deve remover ou desabilitar o ponto de interrupção antes do término de função.  
  
 Pontos de interrupção de dados não funcionam sob estas condições:  
  
-   Um processo que está sendo depurado não grava no local de memória  
  
-   O local da memória é compartilhado entre dois ou mais processos  
  
-   O local da memória é atualizado no kernel. Por exemplo, se a memória é passada para o Windows de 32 bits `ReadFile` função, a memória será atualizada de modo kernel e o depurador não interromperá a gravação na memória.  
  
## Definindo um ponto de interrupção com um endereço de memória \(somente C\+\+ nativo\)  
 Você também pode usar o endereço de um objeto para definir um ponto de interrupção em um método chamado em uma instância específica de uma classe.  Veja um exemplo:  
  
 Por exemplo, dado um objeto do tipo `my_class` com o endereço, você pode definir um ponto de interrupção em um método chamado `my_method` chamado a partir dessa instância.  
  
1.  Defina um ponto de interrupção em algum lugar após essa instância da classe é instanciada.  
  
2.  Localizar o endereço da instância \(vamos dizer tem `0xcccccccc`\).  
  
3.  Clique em **Debug \/ novo ponto de interrupção \/ ponto de interrupção de função** \(ou **ALT \+ F9, B**\).  
  
4.  Adicione o seguinte texto para o **nome da função** caixa:  
  
    ```cpp  
    ((my_class *) 0xcccccccc)->my_method  
    ```  
  
##  <a name="BKMK_Specify_advanced_properties_of_a_breakpoint_"></a> Gerenciando pontos de interrupção  
 Você pode usar o **pontos de interrupção** janela \(**Debug \/ Windows \/ pontos de interrupção**, ou **CTRL \+ ALT \+ B**\) para ver todos os pontos de interrupção que você tenha definido em sua solução:  
  
 ![Breakpoints window](../debugger/media/breakpointswindow.png "BreakpointsWindow")  
  
 O **pontos de interrupção** janela fornece um local central para gerenciar todos os seus pontos de interrupção, que pode ser especialmente útil em uma solução grande ou um cenário complexo de depuração em que os pontos de interrupção são essenciais. Se você precisar salvar ou compartilhar o estado e o local de um conjunto de pontos de interrupção, você pode exportar e importar pontos de interrupção somente a partir de **pontos de interrupção** janela.  
  
##  <a name="BKMK_Specify_a_breakpoint_condition_using_a_code_expression"></a> Pontos de interrupção avançados  
  
## Condições de ponto de interrupção  
 Você pode controlar quando e onde um ponto de interrupção é executada, definindo condições.  
  
1.  Clique no ponto de interrupção ou passe o mouse sobre o ponto de interrupção e escolha o ícone de configurações.  
  
2.  No menu de contexto, selecione **condições**. Isso abre o **configurações de ponto de interrupção** janela:  
  
 ![Breakpoint settings](../debugger/media/breakpointsettings.png "BreakpointSettings")  
  
 Quando você verificar o **condições** caixa, a janela se expande para mostrar os diferentes tipos de condições.  
  
 **Expressão condicional:** quando você seleciona a expressão condicional, você pode escolher duas condições: **é verdadeiro** e **quando alterado**. Escolha **é verdadeiro** se você quiser interromper quando a expressão for satisfeita, ou escolha **quando alterado** se você quiser interromper quando o valor da expressão for alterado.  
  
 No exemplo a seguir, definimos o ponto de interrupção atingido somente quando o valor de `testInt` é **4**:  
  
 ![Breakpoint condition is true](../debugger/media/breakpointconditionistrue.png "BreakpointConditionIsTrue")  
  
 No exemplo a seguir, definimos o ponto de interrupção atingido somente quando o valor de `testInt` alterações:  
  
 ![Breakpoint when changed](../debugger/media/breakpointwhenchanged.png "BreakpointWhenChanged")  
  
 O comportamento de quando o campo alterado é diferente para diferentes linguagens de programação. Se você escolher **quando alterado** para código nativo, o depurador não considerará a primeira avaliação da condição como uma alteração, para que o ponto de interrupção não será atingido na primeira avaliação. Se você escolher **quando alterado** para código gerenciado, o ponto de interrupção é atingido na primeira avaliação depois **quando alterado** está selecionado.  
  
 Se você definir uma condição de ponto de interrupção com sintaxe inválida, será exibida uma mensagem de aviso. Se você especificar uma condição de ponto de interrupção com sintaxe válida mas semântica inválida, uma mensagem de aviso aparece na primeira vez em que o ponto de interrupção é atingido. Em ambos os casos, o depurador interromperá a execução quando o ponto de interrupção inválido for atingido. O ponto de interrupção é ignorado somente se a condição é válida e avaliada como `false`.  
  
 A condição pode ser qualquer expressão válida que é reconhecida pelo depurador. Para obter mais informações sobre expressões válidas, consulte [Expressões no depurador](../debugger/expressions-in-the-debugger.md).  
  
## Usando IDs de objeto em condições de ponto de interrupção \(c\# e F \#\)  
 Há momentos em que você deseja observar o comportamento de um objeto específico; Por exemplo, você talvez queira saber por que um objeto foi inserido mais de uma vez em uma coleção. No c\# e F \#, você pode criar IDs de objeto para instâncias específicas de [tipos de referência](/dotnet/csharp/language-reference/keywords/reference-types) e usá\-los em condições de ponto de interrupção. A ID do objeto é gerada pelo common language runtime \(CLR\) serviços de depuração e associada ao objeto.  Para criar uma ID de objeto, faça o seguinte:  
  
1.  Defina um ponto de interrupção no código algum tempo depois que o objeto foi criado.  
  
2.  Inicie a depuração e quando a execução parar no ponto de interrupção, localizar o ponto de interrupção a **locais** janela, clique duas vezes e selecione **Criar ID de objeto**.  
  
     Você deve ver um **$** mais um número no **locais** janela. Isso é o ID do objeto.  
  
3.  Adicione um novo ponto de interrupção condicional no ponto em que você deseja investigar, por exemplo quando o objeto deve ser adicionado à coleção.  
  
4.  Use a ID de objeto no campo expressão condicional. Por exemplo, se houver uma variável `item` consultando o objeto a ser adicionado à coleção, você colocaria **item \= \= $n**, onde **n** é o número de identificação do objeto.  
  
     Execução será interrompida no ponto quando esse objeto deve ser adicionado à coleção.  
  
 Se posteriormente você deseja excluir a ID de objeto, você pode clique a variável no **locais** janela e selecione **Excluir ID de objeto**.  
  
 Observe que os identificadores de objeto criar referências fracas e impede que o objeto que está sendo coletado como lixo. Eles são válidos somente para a sessão de depuração atual.  
  
## Contagem de ocorrências  
 Se você suspeitar que um loop no seu código inicia com comportamento inadequado após um determinado número de iterações, você pode definir um ponto de interrupção para interromper a execução após um número especificado de ocorrências para a para a linha de código associada, em vez de ser forçado a repetidamente pressionar **F5** para atingir o nível de iteração.  
  
 No **configurações de ponto de interrupção** janela, defina a condição como **contagem de ocorrências**. Em seguida, você pode especificar o número de iterações. No exemplo a seguir, definimos o ponto de interrupção atingido em cada iteração outra:  
  
 ![Breakpoint hit count](../debugger/media/breakpointhitcount.png "BreakpointHitCount")  
  
## Filtrar  
 Você pode restringir um ponto de interrupção seja acionado somente em dispositivos especificados ou em threads e processos especificados.  
  
 No **configuração de ponto de interrupção**janela, defina a condição como **filtro**. Insira uma ou mais das expressões a seguir.  
  
-   MachineName \= "name"  
  
-   ProcessId \= valor  
  
-   ProcessName \= "name"  
  
-   ThreadId \= valor  
  
-   ThreadName \= "name"  
  
 Coloque os valores de cadeia de caracteres entre aspas duplas. Você pode combinar cláusulas usando `&` \(AND\), `||` \(OR\), `!` \(NOT\) e parênteses.  
  
##  <a name="BKMK_Print_to_the_Output_window_with_tracepoints"></a> Ações de ponto de interrupção e Tracepoints  
 Um tracepoint é um ponto de interrupção que imprime uma mensagem na janela Saída. Um tracepoint pode funcionar como uma instrução de rastreamento temporária na linguagem de programação.  
  
 No **configurações de ponto de interrupção** janela, verifique o **ações** caixa. Escolha **Log uma mensagem na janela saída** no **ação** grupo. Você pode imprimir uma cadeia de caracteres genérica, como **Este é um teste**. Para incluir o valor de uma variável ou expressão, coloque\-as entre chaves.  
  
 Para interromper a execução quando o tracepoint for atingido, desmarque o **continuar a execução** caixa de seleção. Quando **continuar a execução** estiver marcada, não a execução é interrompida. Em ambos os casos, a mensagem é impressa.  
  
 Você pode usar as seguintes palavras\-chave especial no **mensagem**.  
  
|||  
|-|-|  
|**$ADDRESS**|Instrução atual|  
|**$CALLER**|Nome da função de chamada|  
|**$CALLSTACK**|Pilha de chamadas|  
|**$FUNCTION**|Nome da função atual|  
|**$PID**|Id do processo|  
|**$PNAME**|Nome do processo|  
|**$TID**|Id do thread|  
|**$TNAME**|Nome do thread|  
|**$TICK**||  
|**$TNAME**||  
  
##  <a name="BKMK_Set_a_breakpoint_at_a_function_return_in_the_Call_Stack_window"></a> Rótulos de ponto de interrupção  
 Rótulos de ponto de interrupção são usados somente no **pontos de interrupção** janela para classificar e filtrar a lista de pontos de interrupção. Para adicionar um rótulo a um ponto de interrupção, escolha a linha do ponto de interrupção e escolha **rótulo** no menu de contexto.  
  
## Pontos de interrupção de importação e exportação  
 Você pode exportar um ponto de interrupção em um arquivo XML clicando duas vezes no ponto de interrupção e selecionando **exportar**. O arquivo é salvo por padrão no diretório da solução. Para importar os pontos de interrupção, abra o **pontos de interrupção** janela \(**CTRL \+ ALT \+ B**\) e na barra de ferramentas, clique na seta para a direita \(a dica de ferramenta é **Importar pontos de interrupção de um arquivo**\).  
  
## Solucionar problemas de pontos de interrupção  
  
### Excluí um ponto de interrupção, mas continuar a pressionar ele quando iniciar a depuração novamente  
 Se você excluir um ponto de interrupção durante a depuração, em alguns casos você pode atingir o ponto de interrupção novamente na próxima vez que você iniciar a depuração. Para interromper a alcançar este ponto de interrupção, certifique\-se de todas as instâncias do ponto de interrupção são removidas do **pontos de interrupção** janela.  
  
### O depurador não pode localizar a versão correta do arquivo de origem para um ponto de interrupção  
 Se um arquivo de origem foi alterado e a fonte não corresponde ao código que você está depurando, o depurador pode localizar o arquivo de origem que corresponde a um ponto de interrupção, mesmo que o arquivo de origem existe.  
  
1.  Se você quiser que o Visual Studio exiba o código\-fonte que não corresponde à versão você está depurando, escolha **Debug \/ opções e configurações**. Sobre o **depuração\/geral** página, desmarque o **exigem arquivos de origem que correspondam exatamente à versão original** opção.  
  
2.  Você também pode vincular o ponto de interrupção para o arquivo de origem. Selecione o ponto de interrupção e escolha **condições** no menu de contexto. Verificar **permitem que o código\-fonte seja diferente do original** no **configurações de ponto de interrupção** janela.  
  
### Pontos de interrupção não funcionam em uma DLL  
 Você não pode definir um ponto de interrupção em um arquivo de origem quando o depurador não carregou as informações de depuração para o módulo onde o código está localizado. Os sintomas podem incluir mensagens como **o ponto de interrupção não será definido**. O glifo de ponto de interrupção aviso aparece no local do ponto de interrupção. No entanto, esses pontos de interrupção de aviso tornam\-se pontos de interrupção reais quando o código é carregado. Para obter mais informações sobre o carregamento de símbolos, consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## Consulte também  
 [Navegar pelo Código com o Depurador](../debugger/navigating-through-code-with-the-debugger.md)