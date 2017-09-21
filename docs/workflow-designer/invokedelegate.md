---
title: "InvokeDelegate | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "InvokeDelegate Designer"
  - "System.Activities.Statements.InvokeDelegate.UI"
ms.assetid: 289a7498-5127-453f-beb5-05f05b80d26f
caps.latest.revision: 3
caps.handback.revision: 3
ms.author: "sdanie"
manager: "erikre"
---
# InvokeDelegate
O designer de **InvokeDelegate** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.InvokeDelegate> .  
  
## A atividade de InvokeDelegate  
 <xref:System.Activities.Statements.InvokeDelegate> chama um delegate público.  
  
### Usando o designer de atividade de InvokeDelegate  
 O designer de atividade de **InvokeDelegate** pode ser encontrado na categoria de **Primitivas** de **Caixa de Ferramentas**, que é acessada clicando na guia [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] de **Caixa de Ferramentas** \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CRTL\+ALT\+X.\)  
  
 O designer de atividade de **InvokeDelegate** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde as atividades nunca são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.InvokeDelegate> com <xref:System.Activities.Activity.DisplayName%2A> padrão de InvokeDelegate.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **InvokeDelegate** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades de InvokeDelegate  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.InvokeDelegate> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície do designer de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.InvokeDelegate> .  O valor padrão é InvokeDelegate.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.InvokeDelegate.Delegate%2A>|True|O nome de <xref:System.Activities.Statements.ActivityDelegate> a ser chamado quando a atividade executar.  Esta propriedade pode ser editada na superfície de designer.  Esta é uma propriedade imperativa.|  
|<xref:System.Activities.Statements.InvokeMethod.DelegateArguments%2A>|False|A coleção de argumento de representante chamado.  As chaves são os nomes dos objetos de <xref:System.Activities.Statements.ActivityDelegateParameter> em <xref:System.Activities.Statements.ActivityDelegate> e valores são os argumentos cujas ambas as expressões são avaliadas e atribuídas a <xref:System.Activities.Statements.ActivityDelegateParameter> os objetos correspondentes.  Na grade de propriedade, clique no botão de reticências no campo de **DelegateArguments** , ele exibe a caixa de diálogo **DelegateArguments** para permitir que você definir essa propriedade.  Clique no campo de **Criar Argumento** para adicionar os argumentos.|  
  
## Consulte também  
 [How to: Define and consume activity delegates in the Workflow Designer](../workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer.md)