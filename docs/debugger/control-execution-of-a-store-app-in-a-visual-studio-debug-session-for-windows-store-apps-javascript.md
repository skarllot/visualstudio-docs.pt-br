---
title: "Controlar a execu&#231;&#227;o de um aplicativo da Store em uma sess&#227;o de depura&#231;&#227;o do Visual Studio para Aplicativos da Windows Store (JavaScript) | Microsoft Docs"
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
ms.assetid: 60159535-61ec-466a-a4a6-115ec72a8af5
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Controlar a execu&#231;&#227;o de um aplicativo da Store em uma sess&#227;o de depura&#231;&#227;o do Visual Studio para Aplicativos da Windows Store (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esse guia de início rápido demonstra como navegar no depurador do Visual Studio e como exibir o estado do programa em uma sessão.  
  
 Este início rápido é para desenvolvedores que novos na depuração com Visual Studio e para desenvolvedores que querem saber mais sobre como navegar em uma sessão de depuração do Visual Studio. Ele não ensina a arte de depurar a si próprio. As funções no código de exemplo destinam\-se somente a demonstrar os procedimentos de depuração descritos neste tópico. As funções não utilizam as práticas recomendadas de design de aplicativo ou função. Na verdade, você rapidamente descobrirá que as funções e o aplicativo em si, não fazem muita coisa.  
  
 As seções deste início rápido foram projetadas para serem o mais independentes possível, portanto, você pode ignorar qualquer seção que inclua informações com as quais já esteja familiarizado. Você também não precisa criar um aplicativo de exemplo. No entanto, recomendamos que faça isso e tornamos o processo o mais fácil possível.  
  
 **Atalhos de teclado do depurador.** A navegação no depurador do Visual Studio é otimizada tanto para mouse quanto para teclado. Muitas das etapas neste tópico incluem o acelerador de teclado ou a tecla de atalho em um comentário entre parênteses. Por exemplo, \(teclado: F5\) indica que pressionar a tecla F5 inicia ou continua a execução do depurador.  
  
> [!NOTE]
>  **O padrão Módulo**  
>   
>  Aplicativos da Windows Store normalmente usam o *padrão Módulo* em JavaScript para encapsular dados e funções em uma página. O padrão Módulo usa um fechamento único, autoexecutado e anônimo para manter a funcionalidade de página separada do namespace global. Neste tópico, chamamos essa função de *módulo*.  
  
## Neste tópico  
 Você pode aprender como:  
  
 [Criar o aplicativo de exemplo](#BKMK_Create_the_sample_app)  
  
 [Definir e executar até um ponto de interrupção, entrar em uma função e examinar os dados de programa](#BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data)  
  
 [Entrar, passar sobre e sair de funções](#BKMK_Step_into__over__and_out_of_functions)  
  
 [Definir um ponto de interrupção condicional, executar até o cursor e visualizar uma variável](#BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable)  
  
 [Exibir dados da variável na janela Locais](#BKMK_View_variable_data_in_the_Locals_window)  
  
-   [Exibir dados da variável e a cadeia de protótipos de um objeto](#BKMK_View_variable_data_and_the_prototype_chain_of_an_object)  
  
-   [Examinar dados da cadeia do escopo](#BKMK_Examine_scope_chain_data)  
  
 [Navegue até o código usando a janela Pilha de Chamadas](#BKMK_Navigate_to_code_by_using_the_Call_Stack_window)  
  
##  <a name="BKMK_Create_the_sample_app"></a> Criar o aplicativo de exemplo  
 A depuração é focada em código, portanto, o aplicativo de exemplo usa a estrutura do aplicativo da Windows Store apenas para criar um arquivo de origem no qual você possa ver como funciona a navegação em uma sessão de depuração e como examinar o estado do programa. Todo o código que você vai invocar é chamado por meio da função `module` do arquivo default. js. Nenhum controle é adicionado e nenhum evento é tratado.  
  
1.  **Crie um aplicativo JavaScript da Windows Store em branco.** Abra o Visual Studio. Na home page, escolha o link **Novo Projeto**. Na caixa de diálogo **Novo Projeto**, escolha **JavaScript** na lista **Instalados** e, em seguida, escolha **Windows Store**. Na lista de modelos de projeto, escolha **Aplicativo em Branco**. Visual Studio cria uma nova solução e projeto e exibe o arquivo default.htm no editor de códigos.  
  
     Observe os arquivos de script que são carregados para a página.  
  
    -   Os arquivos `base.js` e `ui.js` criam a **Biblioteca do Windows para JavaScript**. A Biblioteca do Windows para JavaScript é um conjunto de arquivos em JavaScript e CSS que tornam mais fácil criar aplicativos da Windows Store usando JavaScript. Use\-a junto com HTML, CSS e o Tempo de Execução do Windows para criar seu aplicativo.  
  
    -   O código começa no arquivo `default.js` .  
  
2.  **Abra o arquivo de origem default.js.** No Gerenciador de Soluções, abra o nó **js** e escolha `default.js`.  
  
3.  **Substitua o conteúdo da página com o código de exemplo.** Exclua todo o conteúdo do arquivo `default.js`. Siga este link: [Código de exemplo de navegação do depurador \(JavaScript\)](../debugger/debugger-navigation-sample-code-javascript.md) e, em seguida, copie o código listado na seção de JavaScript para a área de transferência. \(Escolha **Voltar** no navegador ou do visualizador da ajuda para retornar a esta página de início rápido.\) No editor do Visual Studio, cole o código no `default.js` agora vazio. Escolha **Ctrl\+S** para salvar o arquivo.  
  
 Agora você pode acompanhar os exemplos neste tópico.  
  
##  <a name="BKMK_Set_and_run_to_a_breakpoint__step_into_a_function__and_examine_program_data"></a> Definir e executar até um ponto de interrupção, entrar em uma função e examinar os dados de programa  
 A maneira mais comum de iniciar uma sessão de depuração é escolher **Iniciar Depuração** no menu **Depurar** \(teclado: F5\). O aplicativo é iniciado e continua até que um ponto de interrupção seja atingido, você suspenda a execução manualmente, ocorra uma exceção ou o aplicativo seja encerrado.  
  
 Quando a execução é suspensa no depurador, você pode exibir o valor de uma variável ativa em uma dica de dados pausando o mouse sobre a variável.  
  
 Depois de suspender a execução do aplicativo \(que também é chamado de invadir o depurador\), você controla a maneira como o restante do código do programa é executado. Você pode continuar a linha por linha, movendo de uma chamada de função para a função em si, ou pode executar uma função chamada em uma única etapa. Esses procedimentos são chamados percorrendo o aplicativo. Você também pode retomar a execução padrão do aplicativo, executando até o próximo ponto de interrupção definido ou até a linha em que você posicionou o cursor. Você pode parar a sessão de depuração a qualquer momento. O depurador foi projetado para executar as operações de limpeza necessárias e sair da execução.  
  
###  <a name="BKMK_Example_1"></a> Exemplo 1  
 Neste exemplo, você define um ponto de interrupção no corpo da função `module` em `default.js` enquanto ela chama a primeira das nossas instruções do usuário. Em seguida, você entra na função, exibe valores de variáveis em dicas de dados do depurador e então interrompe a depuração.  
  
1.  **Defina um ponto de interrupção.** Defina um ponto de interrupção na instrução `callTrack = "module function";` que ocorra logo após a chamada para `app.start()`. Escolha a linha na medianiz sombreada do editor de código\-fonte \(teclado: posicione o cursor na linha e escolha a tecla **F9**\).  
  
     O ícone de ponto de interrupção aparece na medianiz.  
  
2.  **Execute até o ponto de interrupção.** Inicie a sessão de depuração, escolhendo **Iniciar Depuração** no menu **Depurar** \(teclado: F5\).  
  
     O aplicativo começa a ser executado e suspende a execução imediatamente antes da instrução na qual você definir o ponto de interrupção. O ícone de linha atual na medianiz identifica o local e a instrução atual é realçada.  
  
     Agora você está no controle da execução do aplicativo e pode examinar o estado do programa conforme percorre as instruções do programa.  
  
3.  **Entrar na função.** No menu **Depurar**, escolha **Entrar** \(teclado: **F11**\).  
  
     ![Entrar em uma linha de código](~/docs/debugger/media/dbg_jsnav_example1_step_into.png "DBG\_JSNAV\_example1\_step\_into")  
  
     Observe que o depurador se move para a próxima linha, que é uma chamada para a função `example1`. Escolha **Entrar** novamente. O depurador vai para a primeira linha de código da função `example1`. A linha realçada não foi sido executada, mas a função foi carregada na pilha de chamadas e a memória para variáveis locais foi alocada.  
  
4.  Quando você entra em uma linha de código, o depurador executa uma das seguintes ações:  
  
    -   Se a próxima instrução não for uma chamada para uma função em sua solução, o depurador executará a instrução, irá para a próxima instrução e suspenderá a execução.  
  
    -   Se a instrução for uma chamada para uma função em sua solução, o depurador irá para a primeira linha da função chamada e então suspenderá a execução.  
  
     Prossiga para entrar nas instruções de `example1` até atingir o ponto de saída. O depurador realça a chave de fechamento da função.  
  
5.  **Exiba os valores de variáveis em dicas de dados.** Prossiga para entrar nas instruções de `example1` até atingir o ponto de saída. O depurador realça a chave de fechamento da função. Quando você pausa o mouse em um nome de variável, o nome e o valor da variável são exibidos em uma dica de dados.  
  
     ![Modo de exibição de valores de variáveis na dica de dados](~/docs/debugger/media/dbg_jsnav_data_tip.png "DBG\_JSNAV\_data\_tip")  
  
6.  **Adicione uma inspeção para a variável callTrack.** A variável `callTrack` é usada em todo este guia rápido para mostrar as funções chamadas nos exemplos. Para facilitar a exibição do valor da variável, adicione\-o uma janela Inspeção. Selecione o nome da variável no editor e, em seguida, escolha **Adicionar Inspeção** no menu de atalho.  
  
     ![Assista a uma variável](~/docs/debugger/media/dbg_jsnav_watch_window.png "DBG\_JSNAV\_watch\_window")  
  
     Você pode inspecionar diversas variáveis em uma janela Inspeção. Os valores de variáveis inspecionadas, como valores em janelas de dica de dados, são atualizados sempre que a execução é suspensa. As variáveis inspecionadas são salvas nas sessões de depuração.  
  
7.  **Pare a depuração.** No menu **Depurar**, escolha **Parar Depuração** \(atalho do teclado: **Shift\+F5**\). Isso encerra a sessão de depuração.  
  
##  <a name="BKMK_Step_into__over__and_out_of_functions"></a> Entrar, passar sobre e sair de funções  
 Em contraste a entrar em uma função chamada por uma função pai, passar sobre uma função executa a função filha e, em seguida, suspende a execução da função de chamada conforme a função pai é retomada. Você pode entrar em uma função quando estiver familiarizado com a maneira como a função funciona e tiver certeza de que sua execução não afetará o problema que você está investigando.  
  
 Passar sobre uma linha de código que não contém uma chamada de função executa a linha da mesma forma que entrar na linha.  
  
 Sair de uma função filha continua a execução da função e então suspende a execução depois de a função retornar à sua função de chamada. Você pode sair de uma função longa quando tiver determinado que o restante da função não é significativo.  
  
 Tanto passar sobre quanto sair de uma função executam a função.  
  
 ![Para sobre e de métodos](~/docs/debugger/media/dbg_basics_stepintooverout.png "DBG\_Basics\_StepIntoOverOut")  
  
###  <a name="BKMK_Example_2"></a> Exemplo 2  
 Neste exemplo, você pode entrar, passar sobre e sair de funções.  
  
1.  **Chame a função example2 na função de módulo.** Edite a função `module` e substitua a linha após `var callTrack = "module function"` por `example2();`.  
  
     ![Chamar a função exemplo2](~/docs/debugger/media/dbg_jsnav_example2.png "DBG\_JSNAV\_example2")  
  
2.  **Execute até o ponto de interrupção.** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **Depurar** \(teclado: F5\). O depurador suspende a execução no ponto de interrupção.  
  
3.  **Passe sobre a linha de código.** No menu **Depurar**, escolha **Passar Sobre** \(teclado: F10\). O depurador executa a instrução `var callTrack = "module function"` da mesma maneira que entrar na instrução.  
  
4.  **Entrar em example2 e example2\_a.** Escolha a tecla **F11** para entrar na função `example2`. Continue a entrar nas instruções `example2` até chegar à linha `var x = example2_a();`. Novamente, entre nessa linha para mover para o ponto de entrada de `example2_a`. Continue a entrar em cada instrução de `example2_a` até retornar a `example2`.  
  
     ![Depurar uma função](~/docs/debugger/media/dbg_jsnav_example2_a.png "DBG\_JSNAV\_example2\_a")  
  
5.  **Passar sobre uma função.** Observe que na próxima linha em `example2`, `var y = example2_a();` é basicamente igual à linha anterior. Você pode passar sobre essa linha com segurança. Escolha a tecla **F10** para a retomada de `example2` para essa segunda chamada para `example2_a`. Observe que a cadeia de caracteres `callTrack` indica que a função `example2_a` foi executada duas vezes.  
  
6.  **Sair de uma função.** Escolha a tecla **F11** para entrar na função `example2_b`. Observe que `example2_b` não é muito diferente de `example2_a`. Para sair da função, escolha **Sair** no menu **Depurar** \(teclado: **Shift\+ F11**\). Observe que a variável `callTrack` indica que `example2_b` foi executado e que o depurador foi retornado para o ponto em que `example2` é retomado.  
  
7.  **Pare a depuração.** No menu **Depurar**, escolha **Parar Depuração** \(atalho do teclado: **Shift\+F5**\). Isso encerra a sessão de depuração.  
  
##  <a name="BKMK_Set_a_conditional_breakpoint__run_to_the_cursor__and_visualize_a_variable"></a> Definir um ponto de interrupção condicional, executar até o cursor e visualizar uma variável  
 Um ponto de interrupção condicional Especifica uma condição que faz o depurador suspender a execução. A condição é especificada por uma expressão de código que pode ser avaliada como true ou false. Por exemplo, você pode usar um ponto de interrupção condicional para examinar o estado do programa em uma função chamada com frequência apenas quando uma variável atingir um determinado valor.  
  
 Executar até o cursor é como configurar um único ponto de interrupção. Quando a execução for suspensa, você poderá selecionar uma linha na origem e retomar a execução até que a linha selecionada seja atingida. Por exemplo, você pode percorrer um loop em uma função e determinar que o código no loop está sendo executado corretamente. Em vez de percorrer cada iteração do loop, você pode executar até o cursor que é posicionado após a execução do loop.  
  
 Às vezes, é difícil ler um valor de variável na linha de uma dica de dados ou em outra janela de dados. O depurador pode exibir cadeias de caracteres, HTML e Xml em um visualizador de texto que apresente uma exibição formatada do valor em uma janela rolável.  
  
###  <a name="BKMK_Example_3"></a> Exemplo 3  
 Neste exemplo, você deve definir um ponto de interrupção condicional para parar em uma iteração específica de um loop e então executar até o cursor que está posicionado após o loop. Você também pode exibir o valor de uma variável em um visualizador de texto.  
  
1.  **Chame a função example3 na função de módulo.** Edite a função `module` e substitua a linha após `var callTrack = "module function";` por `example3();`.  
  
     ![Exemplo 3 de chamada](~/docs/debugger/media/dbg_jsnav_example3.png "DBG\_JSNAV\_example3")  
  
2.  **Execute até o ponto de interrupção.** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **Depurar** \(teclado: **F5**\). O depurador suspende a execução no ponto de interrupção na função `module`.  
  
3.  **Entre na função example3.** Escolha **Entrar** no menu **Depurar** \(teclado: **F11**\) para ir para o ponto de entrada da função `example3`. Continue entrando na função até ter iterado um ou dois loops do bloco `for`. Observe que levaria muito tempo para percorrer todas as 1.000 iterações.  
  
4.  **Defina um ponto de interrupção condicional.** Na medianiz esquerda da janela de código, clique na linha `s += i.toString() + "\n";` e, em seguida, escolha **Condição** no menu de atalho.  
  
     Selecione a caixa de seleção **Condição** e digite `i == 500;` na caixa de texto. Escolha a opção **É verdadeiro** e escolha **OK**. O ponto de interrupção permite verificar o valor à 500ª iteração do loop `for`. Você pode identificar um ícone de ponto de interrupção condicional pela sua cruz branca.  
  
     ![Ícone de ponto de interrupção de Conditonal](~/docs/debugger/media/dbg_jsnav_breakpoint_condition_icon.png "DBG\_JSNAV\_Breakpoint\_Condition\_icon")  
  
5.  **Execute até o ponto de interrupção.** No menu **Depurar**, escolha **Continuar** \(teclado: **F5**\). Pause sobre `i` para confirmar que o valor atual de `i` é 500. Observe também que a variável `s` é representada como uma linha e é muito maior que a janela de dica de dados.  
  
6.  **Visualize uma variável de cadeia de caracteres.** Clique no ícone de lupa na dica de dados de `s`.  
  
     A janela do Visualizador de texto é exibida e o valor da cadeia de caracteres é apresentado como uma cadeia de caracteres de várias linhas.  
  
     ![Depurar o Visualizador de texto](~/docs/debugger/media/dbg_jsnav_text_visualizer.png "DBG\_JSNAV\_Text\_Visualizer")  
  
7.  **Execute até o cursor.** Selecione a linha `callTrack += "->example3";` e, em seguida, escolha **Executar até o Cursor** no menu de atalho \(teclado: **Ctrl\+F10**\). O depurador conclui as iterações do loop e então suspende a execução na linha.  
  
8.  **Pare a depuração.** No menu **Depurar**, escolha **Parar Depuração** \(atalho do teclado: **Shift\+F5**\). Isso encerra a sessão de depuração.  
  
###  <a name="BKMK_Use_Run_to_Cursor_to_return_to_your_code_and_delete_a_breakpoint"></a> Usar Executar até o Cursor para retornar ao seu código e excluir um ponto de interrupção  
 Executar até o cursor pode ser muito útil quando você tiver entrado em código de biblioteca da Microsoft ou terceiros. Embora percorrer o código de biblioteca possa ser informativo, isso geralmente pode demorar muito. E, em geral, você estará muito mais interessado em seu próprio código. Este exercício mostra como fazer isso.  
  
1.  **Defina um ponto de interrupção na chamada app.start.** Na função `module`, defina um ponto de interrupção na linha `app.start()`  
  
2.  **Execute até o ponto de interrupção e entre na função de biblioteca.**  
  
     Quando você entrar em `app.start()`, o editor exibirá o código em `base.js`. Entre em mais algumas linhas.  
  
3.  **Percorra e saia de funções.** Conforme você avança em \(**F10**\) e a sai do código \(**SHIFT\+F11**\) em `base.js`, você pode chegar à conclusão de que examinar a complexidade e o comprimento da função inicial é não o que você deseja fazer.  
  
4.  **Defina o cursor para seu código e execute até ele.** Volte para o arquivo `default.js` no editor de códigos. Selecione a primeira linha de código após `app.start()` \(você não pode executar até um comentário ou uma linha em branco\). Escolha **Executar até o Cursor** no menu de atalho. O depurador continua a execução da função app.start e suspende a execução no ponto de interrupção.  
  
##  <a name="BKMK_View_variable_data_in_the_Locals_window"></a> Exibir dados da variável na janela Locais  
 A janela Locais é um modo de exibição de árvore dos parâmetros e variáveis da cadeia do escopo da função em execução no momento.  
  
###  <a name="BKMK_View_variable_data_and_the_prototype_chain_of_an_object"></a> Exibir dados da variável e a cadeia de protótipos de um objeto  
  
1.  **Adicione um objeto de matriz à função do módulo.** Edite a função `module` e substitua a linha após `var callTrack = "module function"` por `var myArray = new Array(1, 2, 3);`  
  
     ![definição de myArray](~/docs/debugger/media/dbg_jsnav_myarray.png "DBG\_JSNAV\_myArray")  
  
2.  **Execute até o ponto de interrupção.** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **Depurar** \(teclado: **F5**\). O depurador suspende a execução no ponto de interrupção. Entre na linha.  
  
3.  **Abre a janela Locais.** No menu **Depurar**, aponte para **Windows** e, em seguida, escolha **Locais**. \(Teclado: Alt\+4\).  
  
4.  **Examinar as variáveis locais na função do módulo** As janelas de Locais exibem as variáveis da função atualmente em execução \(a função `module`\) como nós de nível superior da árvore. Quando você inserir uma função, o JavaScript criará todas as variáveis e atribuirá a elas um valor de `undefined`. Funções que são definidas na função têm seu texto como um valor.  
  
     ![Janela Variáveis locais](~/docs/debugger/media/dbg_jsnav_locals_window.png "DBG\_JSNAV\_Locals\_window")  
  
5.  **Percorra as definições de callTrack e myArray.** Encontre as variáveis callTrack e myArray na janela Locais. Percorra \(**F10**\) as duas definições e observe que os campos **Valor** e **Tipo** são alterados. A janela Locais realça os valores das variáveis que foram alterados desde a última interrupção.  
  
6.  **Examine o objeto myArray** e expanda a variável `myArray`. Cada elemento da matriz é listado O nó **\[protótipo\]** que contém a hierarquia de herança do objeto `Array`. Expanda esse nó.  
  
     ![Cadeia de protótipos na janela Variáveis locais](~/docs/debugger/media/dbg_jsnav_locals_proto_chain.png "DBG\_JSNAV\_Locals\_proto\_chain")  
  
    -   O nó **Métodos** lista todos os métodos do objeto `Array`.  
  
    -   O nó **\[protótipo\]** contém o protótipo do objeto `Object` do qual `Array` deriva. Os nós **\[protótipo\]** podem ser recursivos. Cada objeto pai em uma hierarquia de objetos é descrito no nó **\[protótipo\]** de seu filho.  
  
7.  **Pare a depuração.** No menu **Depurar**, escolha **Parar Depuração** \(atalho do teclado: Shift\+F5\). Isso encerra a sessão de depuração.  
  
##  <a name="BKMK_Examine_scope_chain_data"></a> Examinar dados da cadeia do escopo  
 A *cadeia de escopo* de uma função inclui todas as variáveis que estão ativas e que podem ser acessadas pela função. Variáveis globais são parte da cadeia de escopo, assim como quaisquer objetos \(incluindo funções\) definidos na função que define a função atualmente em execução. Por exemplo, a variável `callTrack` definida na função `module` de `default.js` pode ser acessada por qualquer função definida na função `module`. Cada escopo é listado separadamente na janela Locais.  
  
-   As variáveis da função que está em execução no momento são listadas na parte superior da janela.  
  
-   As variáveis de cada escopo de função na cadeia de escopo são listadas sob um nó **\[escopo\]** para a função. As funções de escopo são listadas pela sua ordem na cadeia, da função que define a função atual para a função mais externa da cadeia.  
  
-   O nó **\[Globais\]** lista os objetos globais definidos fora de qualquer função.  
  
 Cadeias de escopo podem ser confusas e são mais bem ilustradas pelo exemplo. No exemplo a seguir, você pode ver como a função `module` cria seu próprio escopo e como você pode criar outro nível de escopo criando um fechamento.  
  
###  <a name="BKMK_Example_4"></a> Exemplo 4  
  
1.  **Chame a função example4 da função de módulo.** Edite a função `module` e substitua a linha após `var callTrack = "module function"` por `example4()`:  
  
     ![Chamada Exemplo4](~/docs/debugger/media/dbg_jsnav_example4.png "DBG\_JSNAV\_example4")  
  
2.  **Execute até o ponto de interrupção.** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **Depurar** \(teclado: **F5**\). O depurador suspende a execução no ponto de interrupção.  
  
3.  **Abre a janela Locais.** Se necessário, no menu **Depurar**, aponte para **Windows** e, em seguida, escolha **Locais**. \(Teclado: **Alt\+4**\). Observe que a janela lista todas as variáveis e funções na função `module` e também contém um nó **\[Globais\]**.  
  
4.  **Examine as variáveis globais.** Expanda o nó **\[Globals\]**. Os objetos e as variáveis em Global foram definidos pela biblioteca do Windows para JavaScript. Você pode adicionar suas próprias variáveis ao escopo global.  
  
5.  **Entre no example4 e examine suas variáveis de eu local e escopo** Entre \(teclado: **F11**\) na função `example4`. Uma vez que `example4` é definido na função `module`, a função `module` torna\-se o escopo pai. `example4` pode chamar qualquer uma das funções na função `module` e acessar suas variáveis. Expanda o nó **\[escopo\]** na janela Locais e observe que ele contém as mesmas variáveis da função `module`.  
  
     ![Escopos do método Exemplo4](~/docs/debugger/media/dbg_jsnav_locals_example4_scope.png "DBG\_JSNAV\_Locals\_example4\_scope")  
  
6.  **Entre em example4\_a e examine suas variáveis de local e escopo** Continuar para entrar em `example4` e na chamada para `example4_a`. Observe que as variáveis locais agora são de `example4_a`, e que o nó **\[Escopo\]** continua contendo as variáveis da função `module`. Embora as variáveis de `example4` estejam ativas, elas não podem ser acessadas por `example4_a` e não fazem parte da cadeia de escopo.  
  
7.  **Entre em multipyByA e examine suas variáveis de local e escopo** Percorra o restante de `example4_a` e entre na linha `var x = multilpyByA(b);`.  
  
     A variável de função `multipyByA` foi definida para a `multiplyClosure` função, que é uma *fechamento*. `multipyClosure` define e retorna uma função interna, `mulitplyXby`, e captura \(encerra\) seu parâmetro e variável. Em um fechamento, a função interna retornada tem acesso aos dados da função externa, assim, ela cria seu próprio nível de escopo.  
  
     Quando você entra em `var x = multilpyByA(b);`, vai para a linha `return a * b;` na função interna `mulitplyXby`.  
  
8.  Na janela Locais, somente o parâmetro `b` é listado como uma variável local em `multiplyXby`, mas um novo nível **\[Escopo\]** foi adicionado. Expandindo esse nó, você verá que ele contém os parâmetros, as funções e as variáveis de `multiplyClosure`, incluindo a variável `a` chamada na primeira linha de `multiplyXby`. Uma verificação rápida do segundo nó **\[Escopo\]** revela as variáveis de função do módulo, que `multiplyXby` acessa em sua próxima linha.  
  
     ![Escopos de um fechamento na janela Variáveis locais](~/docs/debugger/media/dbg_jsnav_scope_mulitplyxby.png "DBG\_JSNAV\_scope\_mulitplyXby")  
  
9. **Pare a depuração.** No menu **Depurar**, escolha **Parar Depuração** \(atalho do teclado: **Shift\+F5**\). Isso encerra a sessão de depuração.  
  
##  <a name="BKMK_Navigate_to_code_by_using_the_Call_Stack_window"></a> Navegue até o código usando a janela Pilha de Chamadas  
 A pilha de chamadas é uma estrutura de dados que contém informações sobre as funções que estão em execução no thread atual do aplicativo. Quando você atinge um ponto de interrupção, a janela Pilha de Chamadas exibe uma lista de todas as funções que estão ativas na pilha. A função que está em execução no momento está no topo da lista da janela Pilha de Chamadas. A função que inicia o thread está na parte inferior da lista. As funções entre o topo e a parte inferior mostram o caminho da chamada da função inicial até a função atual.  
  
 Além de mostrar o caminho da chamada até a função em execução no momento, a janela Pilha de Chamadas pode ser usada para navegar para o código no editor de códigos. Essa funcionalidade pode ser valiosa quando você estiver trabalhando com vários arquivos e desejar ir rapidamente para uma função específica.  
  
###  <a name="BKMK_Example_5"></a> Exemplo 5  
 Neste exemplo, você deve entrar em um caminho de chamada que contenha cinco funções definidas pelo usuário.  
  
1.  **Chame a função example5 na função de módulo.** Edite a função `module` e substitua a linha após `var callTrack = "module function";` pela linha `example5();`.  
  
     ![Exemplo 5 de chamada](~/docs/debugger/media/dbg_jsnav_example5.png "DBG\_JSNAV\_example5")  
  
2.  **Execute até o ponto de interrupção.** Inicie a sessão de depuração escolhendo **Iniciar Depuração** no menu **Depurar** \(teclado: **F5**\). O depurador suspende a execução no ponto de interrupção na função de módulo.  
  
3.  **Abra a janela Pilha de Chamadas.** No menu **Depurar**, escolha **Windows** e, em seguida, escolha **Pilha de Chamadas** \(teclado: Alt\+7\). Observe que a janela Pilha de Chamadas mostra duas funções:  
  
    -   **Código global** é o ponto de entrada da função `module` na parte inferior da pilha de chamadas.  
  
    -   **Função anônima** mostra a linha na função `module` em que a execução é suspensa. Essa é a parte superior da pilha de chamadas.  
  
4.  **Entre nas funções para chegar à função example5\_d.** Escolha **Entrar** no menu **Depurar** \(teclado: **F11**\) para executar as chamadas no caminho de chamada até que o ponto de entrada da função example5\_d. Observe que cada vez que uma função chama uma função, o número de linha da função de chamada é salvo e a função chamada é colocada na parte superior da pilha. O número de linha da função de chamada é o ponto em que a função de chamada suspendeu a execução. Uma seta amarela aponta para a função atualmente em execução.  
  
     ![Janela Pilha de chamadas](~/docs/debugger/media/dbg_jsnav_callstack_windows.png "DBG\_JSNAV\_CallStack\_windows")  
  
5.  **Use a janela Pilha de Chamadas para navegar até o código example5\_a e definir um ponto de interrupção.** Na janela Pilha de Chamadas, selecione o item de lista `example5_a` e, em seguida, escolha **Ir para Fonte** no menu de atalho. O editor de código define o cursor na linha de retorno da função. Defina um ponto de interrupção nessa linha. Observe que a linha de execução atual não é alterada. Somente o cursor do editor foi movido.  
  
6.  **Entre em funções e, em seguida, execute até o ponto de interrupção.** Continue entrando em `example5_d`. Observe que, quando você retorna da função, ela é retirada da pilha de chamadas. Pressione **F5** para continuar a execução do programa. Você para no ponto de interrupção criado na etapa anterior.  
  
7.  **Pare a depuração.** No menu **Depurar**, escolha **Parar Depuração** \(atalho do teclado: **Shift\+F5**\). Isso encerra a sessão de depuração.  
  
## Consulte também  
 [Iniciar uma sessão de depuração \(JavaScript\)](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md)   
 [Início rápido: navegação no depurador \(JavaScript\)](../debugger/control-execution-of-a-store-app-in-a-visual-studio-debug-session-for-windows-store-apps-javascript.md)   
 [Guia de início rápido: depurar HTML e CSS](../debugger/quickstart-debug-html-and-css.md)   
 [Disparar eventos de suspensão, retomada e segundo plano para a Windows Store](../debugger/how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)   
 [Depurar aplicativos no Visual Studio](../debugger/debug-store-apps-in-visual-studio.md)