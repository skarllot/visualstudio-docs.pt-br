---
title: "Navegar pelo C&#243;digo com o Depurador | Microsoft Docs"
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
  - "vs.debug.execution"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "depurando [Visual Studio], controle de execução"
  - "execução, controlando no depurador"
  - "depurando"
ms.assetid: 759072ba-4aaa-447e-8e51-0dd1456fe896
caps.latest.revision: 42
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Navegar pelo C&#243;digo com o Depurador
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Há várias maneiras para percorrer seu código no depurador: etapa para ou passar por métodos, executar até um ponto de interrupção ou um local especificado e especifique se deseja restringir a depuração para seu próprio código ou incluir símbolos para depurar código externo.  
  
##  <a name="BKMK_Step_into__over__or_out_of_the_code"></a> Etapa em, acima ou fora do código  
 Um dos procedimentos de depuração mais comuns é *revisão*. Revisão está executando o código uma linha por vez. Ao paralisar a execução, como a execução do depurador a um ponto de interrupção, você pode usar três **Depurar** comandos de menu para percorrer o código:  
  
|Menu Comando|Atalho de teclado|Descrição|  
|------------------|-----------------------|---------------|  
|**Entrar**|**F11**|Se a linha contém uma chamada de função **Step Into** executa a chamada propriamente dita, então é interrompida na primeira linha de código dentro da função. Caso contrário, **Step Into** executa a próxima instrução.|  
|**Depuração parcial**|**F10**|Se a linha contém uma chamada de função **Step Over** executa a função chamada, então é interrompida na primeira linha de código dentro da função chamada. Caso contrário, **Step Into** executa a próxima instrução.|  
|**Sair**|**SHIFT \+ F11**|**Step Out** retoma a execução do seu código até que a função retorna, então divide no ponto de retorno da função de chamada.|  
  
-   Em uma chamada de função aninhada, **Step Into** entra na função aninhada mais profunda. Se você usar **Step Into** em uma chamada como `Func1(Func2())`, o depurador vai para a função `Func2`.  
  
-   O depurador avança realmente com as instruções de código em vez de linhas físicas. Por exemplo um `if` cláusula pode ser gravada em uma linha:  
  
    ```c#  
    int x = 42;  
    string s = "Not answered";  
    if( int x == 42) s = "Answered!";  
    ```  
  
    ```vb  
    Dim x As Integer = 42  
    Dim s As String = "Not answered"  
    If x = 42 Then s = "Answered!"  
    ```  
  
     Quando você entra nessa linha, o depurador trata a condição como uma etapa e a consequência como outra \(neste exemplo, a condição for verdadeira\).  
  
 Para rastrear visualmente a pilha de chamadas ao entrar em funções, consulte [Mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
##  <a name="BKMK_Break_into_code_by_using_breakpoints_or_Break_All"></a> Entrar no código usando pontos de interrupção ou interromper tudo  
 Quando você estiver depurando um aplicativo com o depurador VS, seu aplicativo está em execução ou está no modo de interrupção.  
  
 O depurador interrompe a execução do aplicativo quando a execução atinge um ponto de interrupção ou quando ocorre uma exceção. Você também pode interromper a execução manualmente a qualquer momento.  
  
 Um ponto de interrupção é um sinal que informa o depurador para suspender temporariamente a execução do seu aplicativo em um determinado ponto. Quando a execução é suspensa em um ponto de interrupção, o programa deve estar no modo de interrupção. Entrar no modo de interrupção não pare ou termine a execução do programa; execução pode ser reiniciada a qualquer momento.  
  
 A maioria dos recursos do depurador, como exibir valores de variáveis na janela locais ou avaliar expressões na janela Watch, estão disponíveis somente no modo de interrupção. Todos os elementos de seu aplicativo permanecem \(funções, variáveis e objetos permanecem na memória, por exemplo\), mas seus movimentos e atividades são suspensos. Durante o modo de interrupção, você pode examinar as posições dos elementos e estados para procurar violações ou bugs. Você também pode fazer ajustes para o aplicativo no modo de interrupção  
  
 Você pode configurar pontos de interrupção para suspender a execução com base em várias condições. Consulte [Usando pontos de interrupção](../debugger/using-breakpoints.md). Esta seção descreve duas maneiras básicas de entrar no código.  
  
1.  **Defina pontos de interrupção no código**  
  
     Para definir um ponto de interrupção simple em seu código, abra o arquivo de origem no editor do Visual Studio. Coloque o cursor na linha de código que você deseja parar no e, em seguida, clique na janela de código para ver o menu de contexto e escolha **ponto de interrupção \/ Inserir ponto de interrupção** \(ou pressione **F9**\). O depurador interrompe a execução correta antes da execução da linha.  
  
     ![Definir um ponto de interrupção](../debugger/media/dbg_basics_setbreakpoint.png "DBG\_Basics\_SetBreakpoint")  
  
     Pontos de interrupção no Visual Studio fornecem um conjunto rico de funcionalidades adicionais, como pontos de interrupção condicionais e tracepoints. Consulte [Usando pontos de interrupção](../debugger/using-breakpoints.md).  
  
2.  **Interromper manualmente o código**  
  
     Para interromper a próxima linha de código em um aplicativo executando disponível, escolha **Depurar**, **Interromper tudo** \(teclado: **Ctrl \+ Alt \+ Break**\).  
  
-   Se você estiver depurando com a opção Just My Code ativada, você interromperá na próxima linha de código em seu projeto. Consulte [Restringir o passo ao Just My Code](#BKMK_Restrict_stepping_to_Just_My_Code).  
  
-   Se você estiver depurando vários programas, um ponto de interrupção ou comando interromper tudo afetará todos os programas que estão sendo depurados por padrão. Consulte [Configurar o comportamento de execução de vários processos](../debugger/debug-multiple-processes.md#BKMK_Configure_the_execution_behavior_of_multiple_processes).  
  
-   Se você interromper a execução de código sem origem correspondente ou símbolo \(. PDB\)\), o depurador exibe um **arquivos de origem não encontrado** ou um **símbolos não encontrados** página que pode ajudá\-lo a localizar os arquivos apropriados. Consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
     Se você não pode acessar os arquivos de suporte, você ainda pode depurar as instruções de assembly na janela de desmontagem.  
  
##  <a name="BKMK_Run_to_a_specified_location_or_function"></a> Executar até um local especificado ou função  
 Às vezes você desejará executar em um determinado ponto de código e parar a execução. Se você tiver um ponto de interrupção no local onde você deseja interromper, escolha **Depurar**, **Iniciar depuração** se você não tiver começado a depuração, ou **Depurar**, **continuar**. \(Em ambos os casos **F5** é a tecla de atalho\). O depurador interrompe no próximo ponto de interrupção na execução do código. Escolha **Depurar**, **continuar** até atingir o ponto de interrupção que você deseja.  
  
 Você também pode executar até onde você colocou o cursor no editor de códigos ou executar a função especificada.  
  
 **Executar até o local do cursor**  
  
 Para executar até o local do cursor, coloque o cursor em uma linha executável do código em uma janela de origem. No menu de contexto do editor \(clique com botão direito no editor\), escolha **Executar até o Cursor**.  
  
 **Executar uma função na pilha de chamadas**  
  
 No **pilha de chamadas** janela, selecione a função e escolha **Executar até o Cursor** no menu de contexto. Para rastrear visualmente a pilha de chamadas, consulte [Mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
 **Executar uma função especificada pelo nome**  
  
 Você pode comandar o depurador para executar o aplicativo até alcançar uma função especificada. Você pode especificar a função pelo nome, ou você pode escolher entre a pilha de chamadas.  
  
 Para especificar uma função por nome, escolha **Depurar**, **novo ponto de interrupção**, **Interromper na função**, em seguida, digite o nome da função e outras informações de identificação.  
  
 ![Caixa de diálogo Novo ponto de interrupção](../debugger/media/dbg_execution_newbreakpoint.png "DBG\_Execution\_NewBreakpoint")  
  
 Se a função está sobrecarregada ou em vários namespaces, você pode escolher as funções que você deseja o **Escolher pontos de interrupção** caixa de diálogo.  
  
 ![Escolha a caixa de diálogo pontos de interrupção](../debugger/media/dbg_execution_overloadedbreakpoints.png "DBG\_Execution\_OverloadedBreakpoints")  
  
##  <a name="BKMK_Set_the_next_statement_to_execute"></a> Definir a próxima instrução a executar  
 Depois de quebrar no depurador, você pode mover o ponto de execução para definir a próxima instrução de código a ser executado. Uma seta amarela na margem de uma fonte ou a janela de desmontagem marca o local da próxima instrução a ser executada. Movendo essa seta, você pode ignorar uma parte de código ou retornar a uma linha executada anteriormente. Você pode usar isso para situações como ignorar uma seção de código que contém um bug conhecido.  
  
 ![Exemplo2](../debugger/media/dbg_basics_example2.png "DBG\_Basics\_Example2")  
  
 Para definir a próxima instrução a ser executada, use um dos seguintes procedimentos:  
  
-   Em uma janela de origem, arraste a seta amarela para um local onde você deseja definir a próxima instrução no mesmo arquivo de origem  
  
-   Em uma janela de origem, coloque o cursor na linha que você deseja executar depois e escolha **Definir próxima instrução** no menu de contexto.  
  
-   Na janela de desmontagem, coloque o cursor na instrução de assembly que você deseja executar depois e escolha **Definir próxima instrução** no menu de contexto.  
  
> [!CAUTION]
>  Definir a próxima instrução faz com que o contador de programa vá diretamente para o novo local. Use este comando com cuidado:  
>   
>  -   Instruções entre os pontos de execução antigo e novo não serão executadas.  
> -   Se você mover o ponto de execução para trás, instruções intermediárias não são desfeitas.  
> -   Mover a próxima instrução para outro funcionar ou escopo geralmente resulta em corrupção de pilha de chamadas, causando um erro de tempo de execução ou uma exceção. Se você tentar mover a próxima instrução para outro escopo, o depurador abre uma caixa de diálogo com um aviso e lhe dá a oportunidade de cancelar a operação. No Visual Basic, você não pode mover a próxima instrução para outro escopo ou função.  
> -   No C\+\+ nativo, se você tiver verificações de tempo de execução ativadas, definir a próxima instrução pode causar uma exceção seja gerada quando a execução atingir o final do método.  
> -   Quando editar e continuar estiver ativado, **Definir próxima instrução** falhará se você tiver feito edições que editar e continuar não pode remapear imediatamente. Isso pode ocorrer, por exemplo, se você tiver editado o código dentro de um bloco catch. Quando isso acontecer, você verá uma mensagem de erro que indica que a operação não é suportada.  
  
> [!NOTE]
>  No código gerenciado, você não pode mover a próxima instrução nas seguintes condições:  
>   
>  -   A próxima instrução está em um método diferente do que a instrução atual.  
> -   Depuração foi iniciada usando Just\-In\-Time de depuração.  
> -   Um desenrolamento de pilha de chamadas está em andamento.  
> -   Uma exceção System. StackOverflowException ou System.Threading.ThreadAbortException foi lançada.  
  
 Não é possível definir a próxima instrução enquanto seu aplicativo estiver sendo executado ativamente. Para definir a próxima instrução, o depurador deve estar no modo de interrupção.  
  
##  <a name="BKMK_Restrict_stepping_to_Just_My_Code"></a> Restringir o passo ao Just My Code  
 Às vezes, enquanto você está depurando, convém examinar apenas o código que você tenha escrito e ignorar outro código, como chamadas do sistema. Você pode fazer isso com a depuração Just My Code. Apenas meu código oculta código não\-usuário para que ele não aparece nas janelas do depurador. Quando você entrar, o depurador percorre a qualquer código de não usuário mas não interrompe a ela. Consulte [Apenas Meu Código](../debugger/just-my-code.md).  
  
> [!NOTE]
>  Não há suporte para o Just My Code para projetos de dispositivo.  
  
##  <a name="BKMK_Step_into_system_calls"></a> Etapa em chamadas do sistema  
 Se você carregar símbolos de depuração para o código do sistema e Just My Code não estiver habilitado, você pode entrar em uma chamada do sistema assim como qualquer outra chamada.  
  
 Para acessar arquivos de símbolo da Microsoft, consulte [Usar servidores de símbolo para localizar arquivos de símbolo não no computador local](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine) no [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) tópico.  
  
 Para carregar símbolos para um componente de sistema específico enquanto você está depurando:  
  
1.  Abra a janela de módulos \(teclado: **Ctrl \+ Alt \+ U**\).  
  
2.  Selecione o módulo que você deseja carregar símbolos.  
  
     Você pode informar quais módulos possuem símbolos carregados examinando o **Status do símbolo** coluna.  
  
3.  Escolha **carregar símbolos** no menu de contexto.  
  
##  <a name="BKMK_Step_into_properties_and_operators_in_managed_code"></a> Depurar propriedades e operadores no código gerenciado  
 O depurador considera propriedades e operadores no código gerenciado por padrão. Na maioria dos casos, isso fornece uma melhor experiência de depuração. Para habilitar a depuração em propriedades ou operadores, escolha **Depurar**, **Opções e configurações**. Sobre o **depuração**, **geral** página, desmarque o **etapa propriedades e operadores \(somente gerenciado\)** caixa de seleção