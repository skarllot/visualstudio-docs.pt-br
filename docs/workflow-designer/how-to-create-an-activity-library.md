---
title: "How to: Create an Activity Library | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Create an Activity Library
As atividades personalizados são usadas para modelar seus processos comerciais específicos em um fluxo de trabalho.  O modelo biblioteca de atividade em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] foi fornecido para permite que você crie como atividades personalizados que usam visualmente [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
### Para criar uma biblioteca de atividade de fluxo de trabalho  
  
1.  Inicie o [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  No menu de **Arquivo** , aponte para **Novo**, e selecione **Projeto...**  
  
     A Caixa de diálogo **Novo Projeto** é exibida.  
  
3.  No painel de **Tipos de projeto** , **Fluxo de Trabalho** selecione projetos de **Visual c\#** ou de agrupamentos de **Visual Basic** dependendo de sua preferência de idioma.  
  
4.  No painel de **Modelos** , **Biblioteca de atividade**.  
  
5.  Na caixa de **Nome** , digite um nome descritivo para seu projeto faça\-o fácil identificar.  
  
6.  Na caixa de **Local** , digite o diretório em que você deseja salvar seu projeto ou clique **Procurar** navegar até ela.  
  
7.  Na caixa de **Solução** , digite um nome descritivo para sua solução, clique em **OK**.  
  
    > [!NOTE]
    >  Se você deseja adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra a solução em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], clique com o botão direito do mouse na solução em **Gerenciador de Soluções**, e selecione **Adicionar**, então **Novo Projeto...** para abrir a caixa de diálogo **Novo Projeto** .  Continuar conforme descrito acima neste procedimento.  
  
8.  O modelo de projeto cria uma definição de atividade em XAML.  [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] abre e exibe a tela para a atividade personalizado.  
  
9. Arraste uma atividade de **Caixa de Ferramentas** para a superfície de design para inclui\-la na atividade personalizado.  
  
    > [!CAUTION]
    >  Uma atividade é permitida você só filho no corpo da atividade personalizado; no entanto, a atividade filho pode ser uma atividade de composição, como uma atividade de <xref:System.Activities.Statements.Sequence> ou a atividade de <xref:System.Activities.Statements.Flowchart> .  
  
## Consulte também  
 [Como criar uma atividade](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Creating a Workflow Project](../workflow-designer/creating-a-workflow-project.md)