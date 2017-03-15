---
title: "Invoking the Visual Studio Debugger for Windows Workflow Foundation (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "stepping"
  - "Step Over command"
  - "stepping, commands"
  - "debugging, using workflow debugger"
  - "workflows, debugger"
  - "workflow debugger, starting"
  - "Step In command"
  - "debugger, workflow"
  - "Step Out command"
  - "debugging workflows, starting the debugger"
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Invoking the Visual Studio Debugger for Windows Workflow Foundation (Legacy)
Este tópico descreve como usar o depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] depuração de aplicativos [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Geralmente, você depura fluxos de trabalho herdados assim como você os programas de depuração escritos em outras linguagens de programação do Visual Studio.  Você pode iniciar o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para Windows Workflow Foundation as seguintes maneiras:  
  
-   **Anexar a Processo** Selecione no menu de **Depurar** para selecionar uma instância em execução de fluxo de trabalho dos processos disponíveis.  
  
-   Pressione **F5** para iniciar executar uma instância de fluxo de trabalho, ou para continuar a executar após um ponto de interrupção foi atingido.  
  
## Percorrendo o código  
 O depurador oferece suporte a um dos procedimentos de depuração mais comuns, pisando, que está executando a linha de código por vez.  Há três comandos para depurar código:  
  
-   **Etapa dentro**: Você pode entrar em uma atividade usando **F11**.  O depurador avança em qualquer manipulador que é definido.  Se nenhum manipulador é definido, você vai sobre a atividade, ou com atividades compostas, que contém outras atividades, você vai na primeira atividade executando.  Entrar em manipuladores do designer de código não é suportado para as seguintes atividades: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**, ou **ReplicatorActivity**.  Para depurar os manipuladores associados com essas atividades, você deve colocar pontos de interrupção explícitos no código.  
  
-   **Depuração Circular**: Você pode entrar fora de uma atividade usando **Shift\-F11**.  Depuração fora de uma atividade executa a atividade atual e todas as suas atividades irmãos para a conclusão.  O depurador interrompe no pai de atividade atual.  Para passar para fora de um manipulador de código, o depurador interrompe a atividade com que o manipulador está associado.  
  
-   **Depuração Parcial**: Você pode entrar em uma atividade usando **F10**.  Para entrar em uma atividade composta.  o depurador interrompe no primeiro filho executável de atividade composta.  Para entrar em uma não composição, como uma atividade de **CodeActivity** , o depurador executa a atividade e seus manipuladores associados e interromper\-los na atividade seguir.  Se a atividade que é executada é a atividade filho a última em uma atividade de composição, então após a execução, as quebras do depurador na atividade pai.  
  
## Anexar a um processo  
 Para depurar um fluxo de trabalho anexar a um processo, selecione o processo disponível na caixa de listagem **Processos Disponíveis** na caixa de diálogo **Anexar a Processo** .  Se **Automática: Código de fluxo de trabalho** não é exibido na caixa de texto **Anexar a** , clique em **Selecionar**.  Na caixa de diálogo **Selecionar Tipo de Código** , clique **Depurar estes tipos de código** e selecione **Fluxo de Trabalho**.  Clique **OK** e clique **Anexar**.  
  
## Depuração com F5  
 Se uma DLL do aplicativo e de fluxo de trabalho de host de fluxo de trabalho está localizado em diferentes projetos do Visual Studio, por exemplo, quando você estiver usando uma biblioteca de atividade de fluxo de trabalho, você deve definir o projeto de DLL de fluxo de trabalho como o projeto de inicialização de solução do Visual Studio depurar o fluxo de trabalho usando **F5**.  Você também deve definir o caminho para o aplicativo host na propriedade de **Iniciar programa externo** de projeto de DLL de fluxo de trabalho.  
  
 Para definir um projeto de inicialização no Solution Explorer, clique com o botão direito do mouse no nome do projeto e selecione **Definir como projeto de inicialização**.  Para definir o caminho para o host na propriedade de **Iniciar programa externo** , clique duas vezes no nó de **Propriedades** de projeto de fluxo de trabalho no Solution Explorer e selecione a guia de **Depurar** .  Em **Iniciar Ação**, selecione **Iniciar programa externo** e digite o caminho para o arquivo .exe que está hospedando o fluxo de trabalho que você deseja depurar.  
  
 Se o aplicativo host é definido como o projeto de inicialização, somente o depurador do Visual Studio é invocado depuração; o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para Windows Workflow Foundation não é chamado.  Se o depurador do Visual Studio é usado, somente os pontos de interrupção C\# ou de código Visual Basic estão batidos; os pontos de interrupção definidos no designer de fluxo de trabalho não são batidos.  Por exemplo, um ponto de interrupção que você definiu em uma atividade de <xref:System.Workflow.Activities.ParallelActivity> no designer é atingido se o depurador de [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] para Windows Workflow Foundation é usado, mas não quando você usar o depurador Visual Studio.  
  
## Consulte também  
 [How to: Set Breakpoints in Workflows \(Legacy\)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Debugging Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)