---
title: "How to: Invoke the Workflow Debugger | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Invoke the Workflow Debugger
Geralmente, você depura fluxos de trabalho assim como você os programas de depuração escritos em outras linguagens de programação do Visual Studio.  Você pode iniciar o depurador de fluxo de trabalho das seguintes maneiras:  
  
-   **Anexar a Processo** Selecione no menu de **Depurar** para selecionar o processo host de execução para sua instância de fluxo de trabalho.  Este procedimento é o mesmo que anexar a um processo host no código gerenciado.  
  
-   Pressione **F5** para iniciar executar uma instância de fluxo de trabalho, ou para continuar a executar após um ponto de interrupção foi atingido.  
  
-   Use a depuração remota.  Para obter informações sobre como usar a depuração remota, consulte [como: Ativar depuração remota](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
    > [!NOTE]
    >  Se o aplicativo de fluxo de trabalho se destina a arquitetura x86 e é hospedado em um computador executando um sistema operacional de 64 bits, então a depuração remota não funcionará a menos que [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] está instalado no computador remoto ou o destino para o aplicativo de fluxo de trabalho é alterado para **Any CPU**.  
  
### Percorrendo o código  
  
-   **Etapa dentro**: Você pode entrar em uma atividade usando **F11**.  O depurador avança em qualquer manipulador que é definido.  Se nenhum manipulador é definido, você vai sobre a atividade, ou com atividades compostas, que contém outras atividades, você vai na primeira atividade executando.  
  
-   **Step out:** Você pode entrar fora de uma atividade usando **Shift\-F11**.  Depuração fora de uma atividade executa a atividade atual e todas as suas atividades irmãos para a conclusão.  O depurador interrompe no pai de atividade atual.  Para passar para fora de um manipulador de código, o depurador interrompe a atividade com que o manipulador está associado.  
  
-   **Depuração Parcial**: Você pode entrar em uma atividade usando **F10**.  Para entrar em uma atividade de composição, o depurador interrompe no primeiro filho executável de atividade composta.  Para entrar em uma não composição, como uma atividade de <xref:System.Activities.Statements.Assign> , o depurador executa a atividade e seus manipuladores associados e interromper\-los na atividade seguir.  Se a atividade que é executada é a atividade filho a última em uma atividade de composição, então, após a execução, o depurador interrompe a atividade pai.  
  
### Depuração com F5  
  
-   Se você estiver criando um projeto de aplicativo do console de fluxo de trabalho, pressione **F5** simplesmente iniciar a depuração em seu aplicativo e fluxo de trabalho.  Se você estiver criando uma biblioteca de atividade em seus próprios, você deve ter um executável do aplicativo host como um projeto de inicialização.  Para definir um projeto de inicialização em **Gerenciador de Soluções**, clique com o botão direito do mouse no nome do projeto host e selecione **Definir como projeto de inicialização**.  
  
## Consulte também  
 [How to: Set Breakpoints in Workflows](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [Debugging Workflows with the Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)