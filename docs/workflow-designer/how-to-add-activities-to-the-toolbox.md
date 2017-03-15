---
title: "How to: Add Activities to the Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Add Activities to the Toolbox
As atividades podem ser adicionadas a **Caixa de Ferramentas** em sua solução em várias maneiras diferentes.  Você pode adicioná\-los do seu projeto atual, referênciá\-los de um projeto diferente, ou referênciá\-los de um conjunto diferente.  
  
### Para adicionar uma atividade do seu projeto atual  
  
1.  Adicionar uma nova atividade personalizado ao seu projeto atual de fluxo de trabalho.  [!INCLUDE[crabout](../test/includes/crabout_md.md)] que adiciona uma nova atividade personalizado ao seu projeto, consulta [How to: Add a New Item to a Workflow Project](../Topic/How%20to:%20Add%20a%20New%20Item%20to%20a%20Workflow%20Project.md).  
  
2.  Adicione lógica personalizada para a atividade.  
  
3.  Compile o projeto.  Se a compilação for bem\-sucedida, uma nova categoria no **Toolbox** chamado "\<*nome do projeto*\>" com a atividade personalizado incluída na categoria é exibida.  
  
    > [!NOTE]
    >  Se a caixa de ferramentas é reiniciada, as atividades personalizados serão removidas, mesmo se a solução é compilado novamente.  Para preencher novamente a caixa de ferramentas com atividades personalizados depois que redefinido, reinicie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
    > [!NOTE]
    >  A caixa de ferramentas só pode mostrar uma atividade de um determinado nome.  Se duas atividades diferentes assemblies com o mesmo nome de classe, somente um exibirá.  
  
    > [!NOTE]
    >  O domínio de aplicativo é compartilhado entre instâncias do editor; se as variáveis estáticas são usados, serão compartilhados entre instâncias do editor também.  Se esse não é o comportamento desejado, um serviço deve ser usado para controlar instâncias variáveis.  Consulte [Usando o contexto da edição de ModelItem](../Topic/Using%20the%20ModelItem%20Editing%20Context.md) para obter informações sobre como usar serviços no designer.  
  
### Para adicionar uma atividade de dentro de um projeto diferente  
  
1.  Abra uma solução que contém pelo menos um projeto de fluxo de trabalho e um projeto personalizado de biblioteca de atividade ou outro projeto de fluxo de trabalho que define uma atividade personalizado.  
  
2.  Criar ambos os projetos.  Se as compilações foram bem\-sucedidas, uma nova categoria no **Toolbox** chamado "\<*nome do projeto*\>" com a atividade personalizado incluída na categoria é exibida.  
  
### Para adicionar uma atividade à caixa de ferramentas de um assembly  
  
1.  Abra uma solução de fluxo de trabalho.  
  
2.  No menu de **Ferramentas** , selecione **Escolher itens da Caixa de Ferramentas...**  
  
3.  Na caixa de diálogo **Escolher Itens de Caixa de Ferramentas** , selecione a guia de **Componentes de System.Activities** então clique **Procurar...** para navegar para o assembly que contém a atividade personalizado que você deseja adicionar.  
  
4.  Selecione o conjunto e clique em **OK**.  O componente personalizado de atividade é adicionado à lista de componentes e automaticamente selecionado.  
  
    1.  Clique **OK** para fechar a caixa de diálogo.  
  
5.  Para exibir a caixa de ferramentas, **Caixa de Ferramentas** partir do menu de **Modo de Visualização** .  
  
6.  A atividade personalizado em **Caixa de Ferramentas** apareceu sob a categoria que estava em foco antes que o item foi adicionado.  Por exemplo, se a categoria de **Geral** foi selecionada em **Caixa de Ferramentas** antes de adicionar o item da caixa de ferramentas, a atividade aparece sob a categoria de **Geral** .  
  
## Consulte também  
 [Using the Workflow Designer](../workflow-designer/using-the-workflow-designer.md)