---
title: "How to: Create a WCF Workflow Service Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
caps.handback.revision: 14
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Create a WCF Workflow Service Application
aplicativos de serviço do fluxo de trabalho[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] são serviços de comunicação distribuídos que transmitem as mensagens entre clientes e eles próprios através dos limites de processo.  A implementação do contrato de serviço no lado de serviço é feita declarativamente com as atividades de fluxo de trabalho em [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] de um modo semelhante aos serviços herdados de fluxo de trabalho no .NET Framework 3.5.  
  
### Para criar um aplicativo de serviço do fluxo de trabalho WCF  
  
1.  Inicie o [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  No menu de **Arquivo** , aponte para **Novo**, e selecione **Projeto...**  
  
     A Caixa de diálogo **Novo Projeto** é exibida.  
  
3.  No painel de **Modelos Instalados** , **WCF** selecione ou **Fluxo de Trabalho** de agrupamentos de **Visual c\#** ou de **Visual Basic** como você linguagem de opção.  
  
4.  No painel médio, **Aplicativo de Serviço WCF de Fluxo de Trabalho**.  
  
5.  Na caixa de **Nome** , digite um nome descritivo para seu projeto faça\-o fácil identificar.  
  
6.  Na caixa de **Local** , digite o diretório em que você deseja salvar o projeto, clique em **Procurar** para navegar até ela.  
  
7.  Na caixa de **Solução** , selecione a qualquer um criar uma nova solução e então clique em **OK**.  
  
    > [!NOTE]
    >  Se você deseja adicionar um aplicativo de console do fluxo de trabalho a uma solução existente, abra a solução em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], clique com o botão direito do mouse na solução em **Gerenciador de Soluções**, e selecione **Adicionar**, então **Novo Projeto...** para abrir a caixa de diálogo **Novo Projeto** .  Continuar conforme descrito acima neste procedimento.  
  
8.  O modelo de projeto cria uma definição de serviço como XAML.  [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] abre para o modo design com uma atividade de <xref:System.Activities.Statements.Sequence> que contém um conjunto de <xref:System.ServiceModel.Activities.Receive> e de atividades de <xref:System.ServiceModel.Activities.SendReply> .  
  
## Consulte também  
 [Como criar uma atividade](../Topic/How%20to:%20Create%20an%20Activity.md)   
 [Creating a Workflow Project](../workflow-designer/creating-a-workflow-project.md)