---
title: "InvokeMethod Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.InvokeMethod.UI"
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# InvokeMethod Activity Designer
o designer de**InvokeMethod** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.InvokeMethod> .  
  
## A atividade de InvokeMethod  
 <xref:System.Activities.Statements.InvokeMethod> chama um método público de um objeto ou tipo especificado.  
  
### Usando o designer de atividade de InvokeMethod  
 O designer de atividade de **InvokeMethod** pode ser encontrado na categoria de **Primitivas** de **Caixa de Ferramentas**, que é acessada clicando na guia [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] de **Caixa de Ferramentas** \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CRTL\+ALT\+X.\)  
  
 O designer de atividade de **InvokeMethod** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde as atividades nunca são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.InvokeMethod> com <xref:System.Activities.Activity.DisplayName%2A> padrão de InvokeMethod.  <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **InvokeMethod** ou na caixa de **DisplayName** da grade de propriedade.  
  
### As propriedades de InvokeMethod  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.InvokeMethod> e descreve como elas são usadas no designer.  Essas propriedades podem ser editadas na grade de propriedade e alguns podem ser editados na superfície do designer de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.InvokeMethod> .  O valor padrão é InvokeMethod.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|True|O nome do método a ser chamado quando a atividade executar.  O método chamado deve ser declarado como **public**.  Esta propriedade pode ser editada na superfície de designer.  Esta é uma propriedade imperativa.|  
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|False|A coleção de parâmetros do método chamado.  Os parâmetros devem ser adicionados à coleção na mesma ordem que eles aparecem na assinatura de método.  Na grade de propriedade, clique no botão de reticências no campo de **Parâmetros** , ele exibe a caixa de diálogo **Parâmetros** para permitir que você definir essa propriedade.  Clique no botão de **Criar Argumento** para adicionar os parâmetros.|  
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|False|O valor de retorno de chamada de método.|  
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|True|Especifica se o método é chamado de forma assíncrona.  O valor padrão é **False**.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|False|O objeto que contém o método para chamar.  Esta propriedade pode ser editada na superfície de designer.<br /><br /> <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> ou <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> são necessários para ser definidos.|  
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|False|O tipo de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.  Esta propriedade pode ser editada na superfície de designer.  Esta propriedade deve ser definida somente se o método é chamado estático.|  
  
 Para passar parâmetros como um parâmetro C\# **out** \(por exemplo, `Method1(out myParam)),` você deve usar **OutArgument** em vez de **InOutArgument**  
  
 Os métodos com argumentos chamaram **TargetObject** ou **Result** não pode ser chamado usando a atividade de <xref:System.Activities.Statements.InvokeMethod> .  A razão para isso é que registros de atividade de <xref:System.Activities.Statements.InvokeMethod> <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> e <xref:System.Activities.Statements.InvokeMethod.Result%2A> em <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
 O algoritmo para registrar os parâmetros em <xref:System.Activities.Activity.CacheMetadata%2A> é mostrado na lista a seguir:  
  
1.  Argumento de <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> do registro.  
  
2.  Argumento de <xref:System.Activities.Statements.InvokeMethod.Result%2A> do registro.  
  
3.  Iterar através da coleção de <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> e registrar cada argumento.  
  
 A exceção resultante é do tipo <xref:System.Activities.InvalidWorkflowException> com a seguinte mensagem: “InvokeMethod”: Uma variável, RuntimeArgument ou um DelegateArgument já existem com o nome “TargetObject”.  Nomes devem ser exclusivos dentro do escopo de ambiente.  
  
 Essa limitação não se aplica a <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> e a <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> porque não são argumentos de fluxo de trabalho e portanto não são registrados na coleção de <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> de atividade de <xref:System.Activities.Statements.InvokeMethod> no método de <xref:System.Activities.Activity.CacheMetadata%2A> .  
  
## Consulte também  
 [Primitives](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay](../workflow-designer/delay-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)