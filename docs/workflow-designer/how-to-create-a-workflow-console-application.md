---
title: "How to: Create a Workflow Console Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Create a Workflow Console Application
[!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] permite que você crie fluxos de trabalho para executar o sistema ou processos humanos.  [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] fornece a superfície de design para criar esses fluxos de trabalho.  [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] pode ser usado para criar fluxos de trabalho dentro de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou pode ser integrado em outros aplicativos que rehost o designer.  
  
 Este tópico descreve como usar [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] para criar um fluxo de trabalho em um aplicativo de console.  
  
### Para criar um aplicativo de console do fluxo de trabalho  
  
1.  Inicie o [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  No menu de **Arquivo** , aponte para **Novo**, e selecione **Projeto...**  
  
     A Caixa de diálogo **Novo Projeto** é exibida.  
  
3.  No painel de **Modelos Instalados** , selecione **Fluxo de Trabalho** de agrupamentos de **Visual c\#** ou de **Visual Basic** , dependendo do idioma de preferência.  
  
4.  No painel médio, **Aplicativo de console do fluxo de trabalho**.  
  
5.  Na caixa de **Nome** , digite um nome descritivo para seu projeto faça\-o fácil identificar.  
  
6.  Na caixa de **Local** , digite o diretório em que você deseja salvar o projeto, clique em **Procurar** para navegar até ela.  
  
7.  Na caixa de **Solução** , digite o nome para a nova solução.  Clique **OK** para criar o aplicativo.  
  
    > [!NOTE]
    >  Se você deseja adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra a solução em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], clique com o botão direito do mouse na solução em **Gerenciador de Soluções**, e selecione **Adicionar**, então **Novo Projeto...** para abrir a caixa de diálogo **Novo Projeto** .  Continuar conforme descrito acima neste procedimento.  
  
8.  O modelo de projeto cria uma definição de fluxo de trabalho em XAML e a definição de aplicativo de console está no código\-fonte.  [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] abre e exibe a tela para o fluxo de trabalho que você criou.  
  
9. Para compor um fluxo de trabalho, arraste atividades ou outros itens de fluxo de trabalho **Caixa de Ferramentas** para a superfície de design no fluxo de trabalho.  
  
## Consulte também  
 [Creating a Workflow Project](../workflow-designer/creating-a-workflow-project.md)