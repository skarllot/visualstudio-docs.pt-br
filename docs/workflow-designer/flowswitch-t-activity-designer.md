---
title: "FlowSwitch&lt;T&gt; Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Core.Presentation.FlowSwitchLink.UI"
  - "System.Activities.Statements.FlowSwitch`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLink`1.UI"
  - "System.Activities.Core.Presentation.FlowSwitchLinkIdentifier.UI"
ms.assetid: 5b9c5afe-7499-4ee8-8c33-28aff14bde07
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# FlowSwitch&lt;T&gt; Activity Designer
A atividade de <xref:System.Activities.Statements.FlowSwitch%601> é um nó condicional que fornece a ramificação para o fluxo de controle baseado no critério de correspondência quando mais de duas ramificações alternativas são necessários.  Se a ramificação de fluxo requer apenas dois caminhos, use a atividade de <xref:System.Activities.Statements.FlowDecision> em vez disso.  
  
## A atividade de Flowswitcht \< T \>  
 A atividade de <xref:System.Activities.Statements.FlowSwitch%601> contém <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> que retorna um valor de tipo *T* \(especificado pelo parâmetro genérico\) quando avaliada.  A atividade também contém um conjunto de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>, que especifica um mapeamento exclusivo de resultados possíveis da avaliação a um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> .  <xref:System.Activities.Statements.FlowNode> é executado esse cujo objeto do tipo *T* corresponde ao valor de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>avaliado.  Os exemplos de <xref:System.Activities.Statements.FlowSwitch%601.Default%2A> podem opcionalmente \(\) são fornecidos para casos em que nenhuma correspondência for obtida.  
  
### Usando o Designer de atividade de Flowswitcht \< T \>  
 O **FlowSwitch \< T \>** designer de atividade pode ser encontrado no **fluxograma** categoria do **Toolbox**, que é acessada clicando o **Toolbox** guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL \+ ALT \+ X.\)  
  
 O **FlowSwitch \< T \>** designer de atividade pode ser arrastado do **Toolbox** e ser solto sobre a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície dentro de um **fluxograma** designer de atividade.  Use a janela de **Selecionar Tipos** que exibe para especificar o tipo \(associado no código com <xref:System.Activities.Statements.FlowSwitch%601> pelo parâmetro genérico\) obtido de avaliar <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>.  Este procedimento cria uma atividade de <xref:System.Activities.Statements.FlowSwitch%601> rotulada **Opção** dentro de atividade de <xref:System.Activities.Statements.Flowchart> .  <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> pode ser digitado na caixa de **Expressão** da janela de **Propriedades** clicando em onde o texto de dica que informa “digite uma expressão de VB”.  
  
 Passe o mouse sobre o **FlowSwitch \< T \>** designer de atividade para causar o quadrado que é usado para o link <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> apareça em torno das bordas.  Após arrastar o **FlowSwitch \< T \>** designer de atividade e outros designers de atividade no **fluxograma**, o <xref:System.Activities.Activity> objetos representam estão prontos para ser vinculado juntos para especificar a ordem de execução.  Para criar um do <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> associados a <xref:System.Activities.Statements.FlowSwitch%601>, clique em uma das alças de quadradas dos casos no perímetro da **FlowSwitch \< T \>** e arraste\-a \(segurando o botão do mouse\) para uma das alças que aparece de maneira semelhante ao redor de atividade de destino quando o mouse passa sobre o designer.  Solte o botão do mouse e uma seta do **FlowSwitch \< T \>** para o designer de destino aparece representação desses casos.  O valor padrão para exibe desses casos na seta e nele pode ser editado na caixa de **Maiúscminúsc** da janela de **Propriedades** .  
  
### As propriedades de FlowSwitch \< T \>  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.FlowSwitch%601> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade ou na superfície de designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.FlowSwitch%601.Expression%2A>|True|Especifica a expressão que é avaliada para determinar qual de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> para alternar o caminho execução.|  
|<xref:System.Activities.Statements.FlowSwitch%601.Cases%2A>|False|Especifica um mapeamento exclusivo de resultados possíveis obtidos de avaliar <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> a um conjunto de objetos de <xref:System.Activities.Statements.FlowNode> .|  
|<xref:System.Activities.Statements.FlowSwitch%601.Default%2A>|True|Especificar o mapeamento quando a avaliação de <xref:System.Activities.Statements.FlowSwitch%601.Expression%2A> não coincide com um dos valores contidos no objeto de <xref:System.Activities.Statements.FlowSwitch%601.Cases%2A> .|  
  
## Consulte também  
 [Flowchart](../workflow-designer/flowchart-activity-designers.md)   
 [Flowchart](../workflow-designer/flowchart-activity-designer.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)