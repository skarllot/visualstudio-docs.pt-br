---
title: "Throw Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Throw.UI"
ms.assetid: 5e97c947-be39-4a1f-af04-000e2e09528a
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Throw Activity Designer
O designer de atividade de **Throw** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.Throw> .  
  
## A atividade throw  
 A atividade de <xref:System.Activities.Statements.Throw> gerencie uma exceção.  
  
### Usando o designer de atividade throw  
 O designer de atividade de **Throw** pode ser encontrado na categoria de **Tratamento de Erros** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** no lado esquerdo de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTRL\+ALT\+X.\)  
  
 O designer de atividade de **Throw** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.Throw> com uma opção **DisplayName** throw.  O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **Throw** ou na caixa de **DisplayName** da grade de propriedade.  A propriedade de <xref:System.Activities.Statements.Throw.Exception%2A> deve ser editada na grade de propriedade.  
  
### As propriedades throw  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Throw> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.Throw> .  O padrão é throw.|  
|<xref:System.Activities.Statements.Throw.Exception%2A>|True|A exceção para lançar.  Esta exceção deve derivar de <xref:System.Exception>.  Para especificar a exceção, digite uma expressão do Visual Basic na grade de propriedade.|  
  
## Consulte também  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw Activity Designer](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)