---
title: "Caixa de di&#225;logo Geral, Depura&#231;&#227;o, Op&#231;&#245;es | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.options.General"
  - "VS.ToolsOptionsPages.Debugger.General"
  - "VS.ToolsOptionsPages.Debugger.ENC"
  - "vs.debug.options.ENC"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
helpviewer_keywords: 
  - "caixa de diálogo Opções, depuração"
ms.assetid: b33aee0b-43c3-4c26-8ed4-bc673f491503
caps.latest.revision: 46
caps.handback.revision: 46
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Caixa de di&#225;logo Geral, Depura&#231;&#227;o, Op&#231;&#245;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O**Ferramentas \/ opções \/ depuração \/ geral** página permite que você defina as seguintes opções:  
  
 **Perguntar antes de excluir todos os pontos de interrupção**  
 Requer confirmação antes de concluir o **Excluir todos os pontos de interrupção** comando.  
  
 **Interromper todos os processos quando um processo for interrompido**  
 Interrompe simultaneamente todos os processos ao qual o depurador é anexado, quando ocorre uma interrupção.  
  
 **Interromper quando as exceções cruzarem AppDomain ou limites gerenciados\/nativos**  
 Na depuração gerenciada ou modo misto, o common language runtime pode capturar exceções que ultrapassam os limites de domínio de aplicativo ou limites gerenciados\/nativos quando as seguintes condições forem verdadeiras:  
  
 1\) quando o código nativo chama código gerenciado usando interoperabilidade COM e o código gerenciado lança uma exceção. Consulte [Introdução à interoperabilidade COM](/dotnet/visual-basic/programming-guide/com-interop/introduction-to-com-interop).  
  
 2\) quando o código gerenciado em execução no domínio do aplicativo 1 chama código gerenciado no domínio do aplicativo 2 e o código no domínio do aplicativo 2 lança uma exceção. Consulte [programação com domínios de aplicativo](http://msdn.microsoft.com/pt-br/bd36055b-56bd-43eb-b4d8-820c37172131).  
  
 3\) quando o código chama uma função usando reflexão e a função lançará uma exceção. Consulte [Reflexão](../Topic/Reflection%20in%20the%20.NET%20Framework.md).  
  
 Em 2\) e 3\), às vezes, a exceção é detectada pelo código gerenciado em `mscorlib` em vez do common language runtime. Essa opção não afeta a quebra em exceções capturadas por `mscorlib`.  
  
 **Habilitar depuração no nível do endereço**  
 Habilita recursos avançados para depuração no nível do endereço \(o **desmontagem** janela, o **registra** janela e pontos de interrupção de endereço\).  
  
 **Mostrar desmontagem se a fonte não está disponível**  
 Mostra automaticamente o **desmontagem** janela quando você tenta depurar o código fonte não está disponível.  
  
 **Habilitar filtros de ponto de interrupção**  
 Permite que você defina filtros em pontos de interrupção para que eles afetem somente processos específicos, threads ou computadores.  
  
 **Habilitar o Assistente de exceção**  
 Somente para código gerenciado. Gerenciado exceções abrir a caixa de diálogo Assistente de exceção.  Consulte [Exception Assistant](../Topic/Exception%20Assistant.md).  
  
 **Desenrolar a pilha de chamadas em exceções não tratadas**  
 Faz com que o **pilha de chamadas** janela para reverter a pilha de chamadas para o ponto antes da exceção não tratada.  
  
 **Habilitar Just My Code**  
 O depurador exibe e as etapas no código do usuário \("My Code"\), ignorando o código de sistema e outro código que é otimizado ou que não tem símbolos de depuração.  
  
 **Mostrar todos os membros dos objetos não usuário nas janelas de variáveis \(somente Visual Basic\)**  
 Ativa a exibição de membros não públicos em objetos que estão no código de não usuário \(não "My Code"\).  
  
 **Avisar se não houver código do usuário na inicialização**  
 Quando a depuração começa com Just My Code ativado, esta opção avisa se não há nenhum código de usuário \("meu código"\).  
  
 **Habilitar o .NET Framework depuração da origem**  
 Permite que o depurador entrar na origem do .NET Framework. Habilitar esta opção desabilita automaticamente apenas meu código do .NET Framework símbolos serão baixados para um local de cache. Você pode alterar o local do cache no **opções** caixa de diálogo, **depuração** categoria, **símbolos** página.  
  
 **Depurar propriedades e operadores \(somente gerenciado\)**  
 Impede que o depurador de depuração de propriedades e operadores no código gerenciado.  
  
 **Habilitar a avaliação de propriedade e outras chamadas de função implícitas**  
 Ativa a avaliação automática de propriedades e de função implícitas chama nas janelas de variáveis e o **QuickWatch** caixa de diálogo.  
  
 **Chamar a função de conversão de cadeia de caracteres em objetos em janelas variáveis \(c\# e JavaScript somente\)**  
 Executa uma chamada de conversão de cadeia de caracteres implícita ao avaliar objetos em janelas variáveis. Portanto, esse resultado é exibido como uma cadeia de caracteres em vez do nome do tipo. Aplica\-se somente durante a depuração em código c\#. Essa configuração pode ser substituída pelo atributo DebuggerDisplay \(consulte [Usando o atributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)\).  
  
 **Habilitar o suporte do servidor de origem**  
 Informa o depurador do Visual Studio para obter arquivos de origem de servidores de origem que implementam o SrcSrv \(`srcsrv.dll`\) protocolo. Team Foundation Server e as ferramentas de depuração para Windows são dois servidores de origem que implementam o protocolo. Para obter mais informações sobre a configuração de SrcSrv, consulte a documentação de ferramentas de depuração para Windows. Além disso, consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
> [!IMPORTANT]
>  Como ler arquivos. PDB pode executar código arbitrário em arquivos, certifique\-se de que você confia no servidor.  
  
 **Imprimir mensagens de diagnóstico de servidor de origem na janela Saída**  
 Quando o suporte do servidor de origem está habilitada, essa configuração ativa ao diagnóstico.  
  
 **Permitir que o servidor de origem para assemblies de confiança parcial \(somente gerenciado\)**  
 Quando o suporte do servidor de origem está habilitada, essa configuração substitui o comportamento padrão de não recuperar as fontes para assemblies de confiança parcial.  
  
 **Realçar a linha inteira para pontos de interrupção e instrução atual**  
 Quando o depurador realça um ponto de interrupção ou instrução atual, ele destaca a linha inteira.  
  
 **Requer arquivos de origem correspondam exatamente à versão original**  
 Informa o depurador para verificar se um arquivo de origem corresponde à versão do código\-fonte usado para criar o arquivo executável que você está depurando. Se a versão não corresponde, será solicitado que você localize uma origem correspondente. Se uma origem correspondente não for encontrada, o código\-fonte não será exibido durante a depuração.  
  
 **Redirecionar todo o texto da janela Saída para a janela imediata**  
 Envia todas as mensagens do depurador que normalmente apareceriam no **saída** janela para o **imediato** janela em vez disso.  
  
 **Mostrar estrutura bruta de objetos em janelas variáveis**  
 Desativa todas as personalizações de exibição de estrutura de objeto. Para obter mais informações sobre personalizações de exibição, consulte [Exibindo tipos de dados personalizados](../debugger/create-custom-views-of-dot-managed-objects.md).  
  
 **Suprimir a otimização JIT na carga do módulo \(somente gerenciada\)**  
 Desabilita a otimização JIT de código gerenciado quando um módulo é carregado e JIT é compilado enquanto o depurador é anexado. Desativar a otimização pode facilitar a depuração de alguns problemas, embora às custas do desempenho. Se você estiver usando o Just My Code, suprimindo JIT otimização pode causar o código não\-usuário apareça como código de usuário \("meu código"\).  
  
 **Avisar se não houver símbolos na inicialização \(somente nativo\)**  
 Exibe uma caixa de diálogo de aviso quando você tenta depurar um programa para o qual o depurador não tem nenhuma informação de símbolo.  
  
 **Avisar se a depuração de script está desabilitada na inicialização**  
 Exibe uma caixa de diálogo de aviso quando o depurador é iniciado com a depuração de script desabilitada.  
  
 **Carregar exportações de dll**  
 Carrega as tabelas de exportação de dll. Informações de símbolo de tabelas de exportação de dll podem ser útil se você estiver trabalhando com mensagens do Windows, procedimentos do Windows \(WindowProcs\), objetos COM, ou marshaling ou qualquer dll para o qual você não tem símbolos. Informações sobre exportação de dll de leitura envolve alguma sobrecarga. Portanto, esse recurso está desativado por padrão.  
  
 Para ver quais símbolos estão disponíveis na tabela de exportação de uma dll, use `dumpbin /exports`. Símbolos estão disponíveis para qualquer dll do sistema de 32 bits. Lendo o `dumpbin /exports` de saída, você pode ver o nome exato da função, incluindo caracteres não alfanuméricos. Isso é útil para definir um ponto de interrupção em uma função. Nomes de função de tabelas de exportação de dll podem aparecer truncados em outro lugar no depurador. As chamadas são listadas na ordem de chamada, com a função atual \(a mais profundamente aninhada\) na parte superior. Para obter mais informações, consulte [dumpbin\/exportações](/visual-cpp/build/reference/dash-exports).  
  
 **Mostrar diagrama de pilhas paralelas baixo para cima**  
 Controla a direção na qual as pilhas são exibidas no **pilhas paralelas** janela.  
  
 **Ignorar as exceções de acesso de memória GPU se os dados gravados não altera o valor**  
 Ignora as condições de corrida que foram detectadas durante a depuração caso os dados não foram alterados. Para obter mais informações, consulte [Depurando código de GPU](../debugger/debugging-gpu-code.md).  
  
 **Use o modo de compatibilidade gerenciado**  
 Substitui o padrão do mecanismo com uma versão herdada para habilitar estes cenários de depuração:  
  
-   Você está usando uma linguagem .NET Framework diferente de c\#, VB ou F \#, que fornece seu próprio avaliador de expressão \(Isso inclui C \+ \+ \/ CLI\).  
  
-   Você deseja habilitar editar e continuar para projetos do C\+\+ durante a depuração de modo misto.  
  
 Observe que a modo escolhendo compatibilidade gerenciada desativa alguns recursos que são implementados somente no mecanismo de depuração padrão.  
  
 **Use o modo de compatibilidade nativa**  
 Quando essa opção é selecionada, o depurador usa o depurador nativo do Visual Studio 2010, em vez do novo depurador nativo.  
  
 Você deve usar essa opção quando você estiver depurando código C\+\+ .NET, porque o novo mecanismo de depuração não oferece suporte para avaliar expressões C\+\+ .NET. No entanto, habilitar o modo de compatibilidade nativa desativa muitos recursos que dependem da implementação atual do depurador para operar. Por exemplo, o mecanismo herdado não tem muitos visualizadores para tipos internos como `std::string` em projetos do Visual Studio 2015.   Use projetos do Visual Studio 2013 para a melhor experiência de depuração nesses casos.  
  
 **Use os avaliadores de expressão c\# e VB herdados**  
 O depurador usará os avaliadores de expressão c\# \/VB Visual Studio 2013 C em vez dos avaliadores de expressão com base no Roslyn de 2015 do Visual Studio.  
  
 **Avisar ao usar os visualizadores do depurador personalizados contra código potencialmente não seguro**  
 Visual Studio o avisa quando você estiver usando um visualizador de depurador personalizada que está executando o código do processo de depuração, porque ele pode estar executando o código não seguro.  
  
 **Habilitar o alocador de heap de depuração do Windows \(somente nativo\)**  
 Permite que o heap de depuração do windows melhorar o diagnóstico de heap. Habilitar essa opção afetará o desempenho de depuração.  
  
 **Habilitar ferramentas de depuração para XAML da interface do usuário**  
 A Live Visual Tree e os windows Live propriedade explorar aparecerá quando você iniciar a depuração \(F5\) um tipo de projeto com suporte. Para obter mais informações, consulte [Inspecione as propriedades XAML durante a depuração](../debugger/inspect-xaml-properties-while-debugging.md).  
  
 **Visualizar os elementos selecionados na árvore Visual em tempo real**  
 O elemento XAML cujo contexto está selecionado também está selecionado no **Live Visual Tree** janela.  
  
 **Mostrar ferramentas de tempo de execução no aplicativo**  
 Mostra o **Live Visual Tree** comandos em uma barra de ferramentas na janela principal do aplicativo XAML que está sendo depurado. Essa opção foi introduzida na atualização 2 do Visual Studio 2015.  
  
 **Habilitar ferramentas de diagnóstico durante a depuração**  
 O **Ferramentas de diagnóstico** janela é exibida enquanto você está depurando. Para obter mais informações, consulte [Diagnóstico integrado do depurador](../Topic/Debugger-integrated%20profiling.md).  
  
 **Mostrar PerfTip de tempo decorrido durante a depuração**  
 A janela de código exibe o tempo decorrido de uma chamada de método em questão quando você está depurando.  
  
 **Habilitar Editar e continuar**  
 Você pode usar o editar e continuar funcionalidade durante a depuração.  
  
 **Habilitar nativo editar e continuar**  
 Você pode usar o editar e continuar funcionalidade durante a depuração de código C\+\+ nativo. Para obter mais informações, consulte [Editar e continuar \(Visual C\+\+\)](../debugger/edit-and-continue-visual-cpp.md).  
  
 **Aplicar alterações em continuar \(somente nativo\)**  
 Visual Studio compila automaticamente e aplica as alterações de código pendentes feitas ao continuar o processo de um estado de interrupção. Se não estiver selecionada, você pode optar por aplicar as alterações usando o item "Aplicar alterações de código" no menu Depurar.  
  
 **Avisar sobre código obsoleto \(somente nativo\)**  
 Receba avisos sobre código obsoleto.  
  
 **Permitir pré\-compilação \(somente nativo\)**  
 Pré\-compilação é permitida.  
  
## Consulte também  
 [Depurando no Visual Studio](../debugger/debugging-in-visual-studio.md)