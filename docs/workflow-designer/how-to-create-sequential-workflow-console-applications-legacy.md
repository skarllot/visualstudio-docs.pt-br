---
title: "How to: Create Sequential Workflow Console Applications (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "workflows, console applications"
  - "sequential workflows, console applications"
  - "console applications, sequential workflow"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Create Sequential Workflow Console Applications (Legacy)
Siga estas etapas para criar um projeto de aplicativo de console sequencial de fluxo de trabalho usando [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] herdado fornecido por [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  Use [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] herdado quando você precisa definir como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### Para criar um aplicativo de console sequencial de fluxo de trabalho  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e selecione **Projeto**.  
  
     A Caixa de diálogo **Novo Projeto** é exibida.  
  
3.  Selecione a opção de **o .NET Framework 3.0** ou a opção de **o .NET Framework 3.5** na lista suspensa para baixo na parte superior da janela de **Novo Projeto** acessar o designer herdado.  
  
    > [!NOTE]
    >  A opção padrão em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] é **o .NET Framework 4**.  Essa opção é usada criar aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] que direcionam [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] e usa o designer herdado.  
  
4.  No painel de **Tipos de projeto** , os selecione projetos do Visual c\# ou projetos do Visual Basic \(em **Outros idiomas**\), selecione **Fluxo de Trabalho**.  
  
5.  No painel de **Modelos** , **Aplicativo de console sequencial de fluxo de trabalho**.  
  
6.  Na caixa de **Nome** , digite um nome descritivo para seu projeto faça\-o fácil identificar.  
  
7.  Na caixa de **Local** , digite o diretório em que você deseja salvar o projeto, clique em **Procurar** para navegar até ela.  
  
     O designer do Windows Forms abre e exibe o Form1 do projeto que você criou.  
  
8.  Clique em **OK**.  
  
     Designer de Fluxo de Trabalho abre e exibe a superfície de design de fluxo de trabalho de fluxo de trabalho sequencial que você criou.  
  
9. Arraste uma atividade de **Caixa de Ferramentas** para a superfície de design em **Atividade de soltar** designado área.  
  
## Consulte também  
 [Creating Legacy Workflow Projects](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/pt-br/557bcb1f-a7ab-49f6-8df7-2706b7001301)