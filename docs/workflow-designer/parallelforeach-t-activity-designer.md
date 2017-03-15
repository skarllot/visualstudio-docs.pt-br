---
title: "ParallelForEach&lt;T&gt; Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ParallelForEach`1.UI"
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ParallelForEach&lt;T&gt; Activity Designer
A atividade de <xref:System.Activities.Statements.ParallelForEach%601> enumera os elementos de uma coleção e executa uma declaração inserido para cada elemento da coleção paralelamente, que está de forma assíncrona no mesmo segmento.  Use esta atividade do controle de fluxo em vez de atividade de <xref:System.Activities.Statements.Sequence> se as atividades filhos desta atividade são esperadas ir ociosa.  
  
 A atividade de <xref:System.Activities.Statements.ParallelForEach%601> tem uma propriedade de <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> que contém uma expressão especificada usuário de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .  A atividade de <xref:System.Activities.Statements.ParallelForEach%601> avalia essa propriedade após cada ramificação completa.  Se for avaliada como **true**, então a atividade de <xref:System.Activities.Statements.ParallelForEach%601> concluída sem executar outros ramificações.  Se <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> não for avaliada como **true**, então a atividade de <xref:System.Activities.Statements.ParallelForEach%601> termina quando todas as atividades filhos terminar.  
  
## A atividade de ParallelForEach \< T \>  
 <xref:System.Activities.Statements.ParallelForEach%601> enumera os valores e agendamento <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> para cada valor que enumera sobre.  Agenda somente <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>.  Como o corpo executa depende se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> vai ociosa.  
  
 Se <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> não vai ociosa, executa em uma ordem inversa como as atividades agendados são tratadas como uma pilha, a atividade agendada a última executa primeiro.  Por exemplo, se você tiver uma coleção de {1,2,3,4} em <xref:System.Activities.Statements.ParallelForEach%601> e usa **WriteLine** como o corpo para gravar o valor.  Você tem 4, 3, 2, 1 \- out impresso no console.  Isso ocorre porque **WriteLine** não vai ociosa logo após 4 atividades de **WriteLine** obteram agendada, sua execução usando um comportamento da pilha \(primeiro no último para fora.\)  
  
 Mas se você tiver atividades em <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> que pode ir ociosa, como uma atividade de <xref:System.ServiceModel.Activities.Receive> ou a atividade de <xref:System.Activities.Statements.Delay> .  Em seguida não há necessidade de esperar que eles terminem concluir.  <xref:System.Activities.Statements.ParallelForEach%601> vá para a atividade e tente agendados seguintes corpo de executá\-lo.  Se a atividade ociosa vai além disso, <xref:System.Activities.Statements.ParallelForEach%601> move novamente em atividade de corpo seguir.  
  
### Usando o Designer de atividade de ParallelForEach \< T \>  
 O **ParallelForEach \< T \>** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **Toolbox**, que é acessada clicando o **Toolbox** guia no lado esquerdo do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL \+ ALT \+ X.\)  
  
 O **ParallelForEach \< T \>** designer de atividade pode ser arrastado do **Toolbox** e ser solto sobre a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que os designers de atividade são colocados normalmente, por exemplo, dentro de um **seqüência** designer de atividade.  Após solto na [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], cria uma atividade de <xref:System.Activities.Statements.ParallelForEach%601>, que contém por padrão <xref:System.Activities.Activity.DisplayName%2A> de **ParallelForEach\<Int32\>.**  
  
### Propriedades de ParallelForEach \< T \> no Designer de fluxo de trabalho  
 A tabela a seguir mostra as propriedades mais úteis de atividade de <xref:System.Activities.Statements.ParallelForEach%601> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável para exibição do designer de atividade no cabeçalho.  O valor padrão é **ParallelForEach\<Int32\>**.  O valor opcionalmente pode ser editado na grade de **Propriedades** ou diretamente no cabeçalho do designer de atividade.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|A atividade a executar para cada item na coleção.  Para adicionar o <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> atividade, soltar uma atividade na caixa de ferramentas para a **corpo** caixa de **ParallelForEach \< T \>** designer de atividade com texto de dica "Descartar atividade aqui".|  
|**TypeArgument**|True|O tipo dos itens na coleção de <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> especificado pelo parâmetro genérico *T*.  Por padrão, **TypeArgument** é definido como **Int32**.  Para alterar o tipo T no **ParallelForEach \< T \>** designer de atividade, alterar o valor da **TypeArgument** caixa de combinação na grade de propriedade.|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|A coleção de itens para iterar.  Para definir a <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, digite um [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] expressão no **valores** caixa a **ForEach \< T \>** designer de atividade na caixa com o texto de dica "Inserir uma expressão VB" ou em **valores** caixa a **propriedades** janela.|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Avaliado após cada iteração completa.  Se avalia para retificar, então o agendada durante iterações é cancelado.  Se esta propriedade não for definida, todas as instruções agendados executam até a conclusão.|  
  
 Por padrão, o iterador do loop é chamado item.  Você pode alterar o nome da variável no iterador o **ForEach** caixa **ParallelForEach \< T \>** designer de atividade.  O iterador do loop pode ser usado em expressões nos filhos de atividade de <xref:System.Activities.Statements.ParallelForEach%601> .  
  
## Consulte também  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)