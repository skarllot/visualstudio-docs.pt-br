---
title: "How to: Set Breakpoints in Workflows (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "breakpoints, setting in workflows"
  - "debugging, setting breakpoints in workflows"
  - "debugging workflows, setting breakpoints"
  - "workflows, setting breakpoints"
ms.assetid: 78e0be39-3e99-487c-bfef-19db0daf6f42
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Set Breakpoints in Workflows (Legacy)
Este tópico descreve como definir pontos de interrupção na construção de aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando seu aplicativo de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Quando você usa [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] para criar um aplicativo de [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] , você pode definir pontos de interrupção em C\# e em código Visual Basic como você faz no Visual Studio.  Como esperado, a execução de fluxo de trabalho que ele pare em cada ponto de interrupção esse definido.  
  
 Um ponto de interrupção tem três estados: *Pendente*, *associado*, e *erro*.  Quando você definir um ponto de interrupção, ele está pendente, e ele é representado por um ícone oco vermelho.  Quando o tempo de execução carregado o tipo de fluxo de trabalho, transformações e limite é representado por um ícone vermelho contínuo.  Se você especificar um formato incorreto do ponto de interrupção, como um nome de atividade que não é válida, uma janela de erro aparece.  O ponto de interrupção é adicionado ainda para a janela de ponto de interrupção, mas é marcado com um pequeno “x”.  
  
 Você pode definir pontos de interrupção em uma atividade na superfície de design de fluxo de trabalho das seguintes maneiras:  
  
-   Clique com o botão direito do mouse na atividade e selecione **Ponto de interrupção \\ ponto de interrupção de inserção**.  
  
-   Selecione a atividade e pressione F9.  
  
-   **Novo Ponto de Interrupção** Partir do menu de **Depurar** .  
  
     Você também pode usar esta opção para definir um novo ponto de interrupção a depuração, quando o depurador para em um ponto de interrupção.  
  
    > [!NOTE]
    >  Os pontos de interrupção em fluxos de trabalho chamados não são suportados.  
  
### Para definir um ponto de interrupção usando a nova opção de ponto de interrupção no menu debug  
  
1.  No menu de **Depurar** , **Novo Ponto de Interrupção**.  
  
2.  Clique **Interromper na Função**.  
  
     A caixa de diálogo **Novo Ponto de Interrupção** abre.  
  
3.  Especifique o nome de uma atividade na caixa de texto **Função** usando essa sintaxe: `QualifiedActivityId[:[FullClassName][:InstanceId]]`.  
  
    > [!NOTE]
    >  Opcionalmente, em vez de usar o nome de atividade na caixa de texto **Função** , você pode definir um ponto de interrupção especificando o caminho absoluto de atividade de fluxo de trabalho.  Por exemplo, suponha que você tenha uma solução de fluxo de trabalho chamada **WorkflowConsoleApplication1** e um fluxo de trabalho na solução chamada **Workflow1** que usa uma atividade chamada **Delay1**.  Você pode usar o nome de atividade **Delay1** ou especifique o caminho como **Delay1: WorkflowConsoleApplication1.Workflow1** ou **Delay1: WorkflowConsoleApplication1.Workflow1: {} 6614886A\-608E\-412B\-BF98\-99FF1559DDDF**.  
  
4.  Selecione a caixa de seleção **Use o IntelliSense** para verificar o nome da função.  
  
     Se esta caixa de seleção não estiver selecionada, nenhuma verificação do nome do ponto de interrupção é executada.  
  
5.  **Fluxo de Trabalho** A partir da lista de **Idioma** .  
  
6.  Clique em **OK**.  
  
## Consulte também  
 [Debugging Legacy Workflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Invoking the Visual Studio Debugger for Windows Workflow Foundation \(Legacy\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)