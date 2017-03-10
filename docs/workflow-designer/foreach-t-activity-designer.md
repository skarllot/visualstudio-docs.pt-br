---
title: "ForEach&lt;T&gt; Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ForEach`1.UI"
ms.assetid: 67097b3a-fcf5-4a72-beb1-2c7784151a86
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ForEach&lt;T&gt; Activity Designer
A atividade de <xref:System.Activities.Statements.ForEach%601> executa a atividade contida em seu <xref:System.Activities.Statements.ForEach%601.Body%2A> para cada item em uma coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificada.  
  
## Propriedades de ForEach \< T \> no Designer de fluxo de trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ForEach%601> e descreve como usá\-los no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.ForEach%601> .  O padrão é \< Int32 \> ForEach.  Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.ForEach%601.Values%2A>|True|A coleção de itens para iterar.  Para definir a <xref:System.Activities.Statements.ForEach%601.Values%2A>, digite um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expressão no **valores** caixa a **ForEach \< T \>** atividade designer ou na grade de propriedade.|  
|*TypeArgument*|True|O tipo dos itens na coleção de <xref:System.Activities.Statements.ForEach%601.Values%2A> especificado pelo parâmetro genérico *T*.  Por padrão, *TypeArgument* é definido como **Int32**.  Para alterar o tipo, altere o valor de caixa de combinação de *TypeArgument* na grade de propriedade.|  
  
 Por padrão, o iterador do loop é chamado **item**.  Você pode alterar o nome da variável de iterador no designer de atividade de <xref:System.Activities.Statements.ForEach%601> .  O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ForEach%601> .  
  
## Consulte também  
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)