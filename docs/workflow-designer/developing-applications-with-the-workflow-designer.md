---
title: "Developing Applications with the Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "DefaultWorkflowDesigner"
  - "DefaultWorkflowDesigner.UI"
helpviewer_keywords: 
  - "Visual Studio 2010 Workflow Designer [WFD], overview"
  - "Workflow Designer [WFD]"
  - "Visual Studio 2010 Workflow Designer [WFD]"
  - "Workflow Designer [WFD], overview"
ms.assetid: 4cd062b1-b496-4668-bbc1-ee85545e066d
caps.latest.revision: 17
caps.handback.revision: 17
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Developing Applications with the Workflow Designer
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] é um designer e um depurador visuais para a compilação e gráficos a depuração de aplicativos de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] em [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] que está hospedada no ambiente de desenvolvimento de [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] .  Permite que você escreve um aplicativo de fluxo de trabalho, uma biblioteca de atividade, ou um serviço composto de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] com o uso de modelos e os designers de atividade.  fluxos de trabalho de[!INCLUDE[crabout](../test/includes/crabout_md.md)] , consulte [O Windows Foundation Workflow o .NET Framework &#91;4&#93;](../Topic/Windows%20Workflow%20Foundation.md).  
  
 Os seguintes são vários novos recursos de design esse conjunto essa nova versão de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] independentemente das versões anteriores de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]:  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] é compilado usando [!INCLUDE[avalon1](../workflow-designer/includes/avalon1_md.md)].  Isso melhora a experiência do designer de atividade e melhora o desempenho para grandes e fluxos de trabalho complexos.  
  
-   As atividades personalizados são criadas agora com [!INCLUDE[avalon2](../workflow-designer/includes/avalon2_md.md)], usando XAML e o modelo de programação para criar designer de atividade foi simplificado.  
  
-   Uma atividade do fluxograma era implementado, então você pode visualizar o fluxo de programa usando o fluxograma familiar que modela o estilo.  
  
-   [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] tem um novo designer variável que permite que você declare e defina o escopo variáveis em seus fluxos de trabalho, associando os às atividades.  
  
-   Em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fornece recursos do IntelliSense para criar expressões do Visual Basic dentro dos fluxos de trabalho [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] .  
  
-   A experiência de depuração estende agora em XAML, permitindo que você defina pontos de interrupção na definição de fluxo de trabalho XAML e entrar no seu código XAML em tempo de execução, que fornece uma experiência semelhante ao código gerenciado.  
  
-   Rehosting [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] fora de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] é simplificado extremamente em comparação com versões anteriores, que requer agora apenas algumas linhas de código.  
  
-   A nova atividade de <xref:System.Activities.Statements.Flowchart> e seu [Flowchart](../workflow-designer/flowchart-activity-designer.md) permitem que você visualize o fluxo de programa usando o fluxograma familiar que modela o estilo.  
  
-   As atividades de mensagem foram aprimoradas, permitindo que você escreva \(nenhum código declarativo completa\) serviços de [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] .  
  
-   A funcionalidade de **Adicionar referência de serviço...** permite que você gerencia as atividades automaticamente que acessam serviços da Web.  
  
## Nesta seção  
 [Using the Workflow Designer](../workflow-designer/using-the-workflow-designer.md)  
 Mostra como criar novos atividades e fluxo de trabalho usando os projetos designer internos e como usar outras ferramentas fornecidas pelo designer para argumentos, a variáveis, para expressões, as importações, e a navegação de trilha de manipular.  
  
 [Using the Activity Designers](../workflow-designer/using-the-activity-designers.md)  
 Descreve as categorias de atividades e modelos e seus designers que são sistema fornecidos.  
  
 [Debugging Workflows with the Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)  
 Descreve como executar procedimentos de depuração bem como a depuração XAML e expressões tradicionais.  
  
 [Workflow Designer UI Help](../workflow-designer/workflow-designer-ui-help.md)  
 Contém tópicos da ajuda contextual para as caixas de diálogo fornecidas por [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)], bem como orientação sobre recursos, em atalhos de teclado e de mensagens de erro do shell de designer.  
  
 [Developing Workflow Applications Targeting the .NET 3.0 or .NET 3.5 Framework](../workflow-designer/developing-workflow-applications-targeting-the-dotnet-3-0-or-dotnet-3-5-framework.md)  
 Contém a orientação sobre como usar o designer herdado que direciona [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 [O designer ReHosting &#91;exemplos de WF&#93;](../Topic/Designer%20ReHosting.md)  
 Este exemplo mostra como criar o layout de WPF para conter o designer.  
  
 [O designer personalizadas da atividade](../Topic/Custom%20Activity%20Designers.md)  
 Esta seção contém exemplos de atividade que usam designer personalizadas para exibição no designer de fluxo de trabalho.