---
title: "Como usar a janela Pilha de Chamadas | Microsoft Docs"
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
  - "vs.debug.callstack"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "aspx"
helpviewer_keywords: 
  - "pontos de interrupção, janela de Pilha de Chamadas"
  - "janela de Pilha de Chamadas, exibindo código de desmontagem para funções na pilha de chamadas"
  - "janela de Pilha de Chamadas, exibindo código-fonte para funções na pilha de chamadas"
  - "depurando [Visual Studio], janela de Pilha de Chamadas"
  - "depurando [Visual Studio], alternando para outro registro de ativação"
  - "código de desmontagem"
  - "funções [depurador], exibindo código na pilha de chamadas"
  - "stack, trocando registros de ativação"
  - "threading [Visual Studio], exibindo chamadas para ou de"
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Como usar a janela Pilha de Chamadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ao usar a janela **Pilha de chamadas**, você pode exibir chamadas de função ou procedimento que estão na pilha atualmente.  
  
 A janela **Pilha de chamadas** exibe o nome de cada função e da linguagem de programação em que ela foi gravada.  O nome da função ou do procedimento pode ser acompanhado de informações opcionais, como o nome do módulo, o número da linha e os nomes de parâmetro, tipos e valores.  A exibição dessas informações opcionais pode ser ativada ou desativada.  
  
 Uma seta amarela identifica o quadro de pilha onde o ponteiro de execução está localizado atualmente.  Por padrão, esse é o quadro cujas informações aparecem na origem, nas janelas **Desmontagem**, **Locais**, **Inspeção** e **Autos**.  Se você desejar alterar o contexto para outro quadro na pilha, poderá fazer isso na janela **Pilha de chamadas**.  
  
 Ao depurar símbolos que não estão disponíveis para a parte de uma pilha de chamadas, a janela **Pilha de chamadas** não poderá exibir as informações corretas para essa parte da pilha de chamadas.  A notação a seguir aparece:  
  
 \[Os quadros abaixo podem estar incorretos e\/ou ausentes, nenhum símbolo carregado para name.dll\]  
  
 No código gerenciado, por padrão, a janela **Pilha de chamadas** oculta informações do código que não seja do usuário.  Aparecerá as notações a seguir em vez das informações ocultas:  
  
 **\[\<External Code\>\]**  
  
 Um código que não seja do usuário é qualquer código que não seja "Meu Código". Você pode optar por exibir informações da pilha de chamadas para o código que não é do usuário usando o menu de atalho.  
  
 Ao usar o menu de atalho, você pode escolher se exibe chamadas entre threads.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos do menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da edição ou das configurações ativas.  Para alterar as configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas**.  Para obter mais informações, consulte [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/pt-br/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para exibir a janela Pilha de chamadas no modo de interrupção ou no modo de execução  
  
-   No menu **Depurar**, selecione **Windows** e clique em **Pilha de chamadas**.  
  
### Para alterar as informações opcionais exibidas  
  
-   Clique com o botão direito do mouse na janela **Pilha de chamadas** e defina ou desmarque **Exibir \<***the information that you want***\>**.  
  
### Para exibir quadros de código de não usuário na janela Pilha de chamadas  
  
-   Clique com o botão direito do mouse na janela **Pilha de chamadas** e selecione **Mostrar Código Externo**.  
  
### Para alternar para outro registro de ativação  
  
1.  Na janela **Pilha de chamadas**, clique com o botão direito do mouse no quadro cujos dados e código você deseja exibir.  
  
2.  Selecione **Alternar para Quadro**.  
  
     Uma seta verde com uma parte final encaracolada aparece ao lado do quadro que você selecionou.  O ponteiro de execução permanece no quadro original, que ainda está marcado com a seta amarela.  Se você selecionar **Etapa** ou **Continuar** no menu **Depurar**, a execução continuará no quadro original, não no quadro selecionado.  
  
### Para exibir chamadas para ou de outro segmento  
  
-   Clique com o botão direito do mouse na janela **Pilha de chamadas** e selecione **Incluir chamadas para\/de outros threads**.  
  
### Para exibir o código\-fonte em uma função na pilha de chamadas  
  
-   Na janela **Pilha de chamadas**, clique com o botão direito do mouse na função cujo código\-fonte você deseja ver e selecione **Ir para Código\-Fonte**.  
  
### Para rastrear visualmente a pilha de chamadas  
  
1.  Na janela **Pilha de chamadas**, abra o menu de atalho.  Escolha **Exibir pilha de chamadas no Mapa de Códigos**. \(Teclado: **CTRL** \+ **SHIFT** \+ **\`**\)  
  
     Consulte [Mapear métodos na pilha de chamadas ao depurar](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### Para exibir o código de desmontagem de uma função na pilha de chamadas  
  
-   Na janela **Pilha de chamadas**, clique com o botão direito do mouse na função cujo código de desmontagem você deseja ver e selecione **Ir para Desmontagem**.  
  
### Para executar em uma função específica da janela de pilha de chamadas  
  
-   Consulte [Executar em um local ou função especificada](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Run_to_a_specified_location_or_function).  
  
### Para definir um ponto de interrupção no ponto de saída de uma chamada de função  
  
-   Consulte [Definir um ponto de interrupção em uma linha de fonte, instrução de assembly ou função de pilha de chamadas](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_at_a_source_line__assembly_instruction__or_call_stack_function_).  
  
### Para carregar símbolos para um módulo  
  
-   Na janela **Pilha de chamadas**, clique com o botão direito do mouse no quadro que mostra o módulo cujos símbolos você deseja recarregar e selecione **Carregar Símbolos**.  
  
## Carregando símbolos  
 Na janela **Pilha de chamadas**, você pode carregar símbolos de depuração para o código que atualmente não tem símbolos carregados.  Esses símbolos podem ser símbolos do .NET Framework ou do sistema baixados dos servidores públicos de símbolo da Microsoft ou de símbolos em um caminho de símbolo no computador que você está depurando.  
  
 Consulte [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### Para carregar símbolos  
  
1.  Na janela **Pilha de chamadas**, clique com o botão direito do mouse no quadro para o qual os símbolos não foram carregados.  O quadro ficará esmaecido.  
  
2.  Aponte para **Carregar Símbolos de** e depois clique em **Servidores de Símbolo Microsoft** ou em **Caminho do Símbolo**.  
  
#### Para definir o caminho do símbolo  
  
1.  Na janela **Pilha de chamadas**, escolha **Configurações de Símbolo** no menu de atalho.  
  
     A caixa de diálogo **Opções** abre e a página **Símbolos** é exibida.  
  
2.  Clique em **Configurações de Símbolo**.  
  
3.  Na caixa de diálogo **Opções**, clique no ícone da Pasta.  
  
     Na caixa **Locais do arquivo de símbolo \(.pdb\)**, um cursor será exibido.  
  
4.  Digite um nome de caminho de diretório no local do símbolo no computador que você está depurando.  Para depuração local, este é o computador local.  Para depuração remota, é o computador remoto.  
  
5.  Clique em **OK** para fechar a caixa de diálogo **Opções**.  
  
## Consulte também  
 [Código misto e informações ausentes na janela Pilha de Chamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Como alterar o formato numérico das janelas do depurador](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)   
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar arquivos de símbolo \(.pdb\) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Usando pontos de interrupção](../debugger/using-breakpoints.md)