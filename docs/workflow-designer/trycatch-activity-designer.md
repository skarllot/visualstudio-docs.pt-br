---
title: "TryCatch Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.TryCatch.UI"
  - "System.Activities.Statements.Catch`1.UI"
ms.assetid: 02a326c2-4009-442f-b7cb-e42121fd2992
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# TryCatch Activity Designer
O designer de atividade de **TryCatch** é usado para criar e configurar uma atividade de <xref:System.Activities.Statements.TryCatch> .  
  
## A atividade de TryCatch  
 A atividade de <xref:System.Activities.Statements.TryCatch> contém uma atividade de <xref:System.Activities.Statements.TryCatch.Try%2A> , uma coleção de **Catch\<TException\>** e uma atividade de <xref:System.Activities.Statements.TryCatch.Finally%2A> .  <xref:System.Activities.Statements.Catch%601> de tipo **TException** contém <xref:System.Activities.Statements.Catch%601.ExceptionType%2A> e <xref:System.Activities.Statements.Catch%601.Action%2A>.  São usados juntos para implementar um mecanismo exceção baseado típico de manipulação de erro.  Uma atividade de <xref:System.Activities.Statements.TryCatch> tentar executar a atividade de <xref:System.Activities.Statements.TryCatch.Try%2A> .  Se a atividade de <xref:System.Activities.Statements.TryCatch.Try%2A> lança uma exceção, a atividade de <xref:System.Activities.Statements.TryCatch> usa sua coleção de **Catch\<TException\>** para coincidir com a exceção.  Se houver uma correspondência, então <xref:System.Activities.Statements.Catch%601.Action%2A> de **Catch\<TException\>** correspondente é executado, servindo como a lógica de manipulação de erro para a exceção.  Se as atividades na seção de <xref:System.Activities.Statements.TryCatch.Try%2A> completa com êxito ou as atividades em <xref:System.Activities.Statements.TryCatch.Catches%2A> completa com êxito, a atividade de <xref:System.Activities.Statements.TryCatch> executa sua atividade de <xref:System.Activities.Statements.TryCatch.Finally%2A> .  [!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Exceções](../Topic/Exceptions.md).  
  
### Usando o designer de atividade de TryCatch  
 O designer de atividade de **TryCatch** pode ser encontrado na categoria de **Tratamento de Erros** de **Caixa de Ferramentas**, que é acessada clicando na guia **Caixa de Ferramentas** no lado esquerdo de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, **Barra de Ferramentas** partir do menu de **Modo de Visualização** , ou CTLR\+ALT\+X.\)  
  
 O designer de atividade de **TryCatch** pode ser arrastado de **Caixa de Ferramentas** e ser solto sobre a superfície de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] onde quer que as atividades são colocadas em geral, como em <xref:System.Activities.Statements.Sequence>.  Isso cria uma atividade de <xref:System.Activities.Statements.TryCatch> com <xref:System.Activities.Activity.DisplayName%2A> padrão de TryCatch.  O valor de <xref:System.Activities.Activity.DisplayName%2A> pode ser editado no cabeçalho do designer de atividade de **TryCatch** ou na caixa de **DisplayName** da grade de propriedade.  Outras propriedades devem ser editadas na superfície do designer de atividade de **TryCatch** .  
  
 Clique no botão expandir no canto direito superior do designer de **TryCatch** para ver **Tentar**, **Catches**, e caixas de **Finalmente** na exibição expandida.  Para adicionar uma captura, clique no botão de **Adicionar nova captura** no designer de **TryCatch** .  O botão muda para uma caixa de combinação de tipo.  Selecione um tipo de exceção e pressione ENTER para adicionar a captura.  Após adicionar **Catch**, a área de captura expande e uma atividade pode ser levada na captura para definir a lógica de execução para a captura.  Observe que há uma caixa de texto no lado direito da área expandida catch.  Você pode nomear a variável de exceções usando esta caixa de texto.  A variável de exceção pode ser usado somente para atividades no mesmo **Catch**.  
  
 O designer de **TryCatch** não suporta editar **Catch**.  Se você desejar alterar o tipo de exceção, você precise excluir **Catch** e adicionar um novo.  **Catch** pode ser excluído e selecionando à exclusão ou usando o menu de **Excluir** no menu de contexto acessado clique direito.  
  
### As propriedades de TryCatch  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.TryCatch> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.TryCatch> .  O padrão é TryCatch.|  
|<xref:System.Activities.Statements.TryCatch.Try%2A>|False|A atividade executada primeiro quando <xref:System.Activities.Statements.TryCatch> executar.|  
|<xref:System.Activities.Statements.TryCatch.Catches%2A>|False|A coleção de elementos de **Catch** a ser selecionados quando a atividade de <xref:System.Activities.Statements.TryCatch.Try%2A> lançar uma exceção.<br /><br /> Você precisa pelo menos de adicionar uma atividade em <xref:System.Activities.Statements.TryCatch.Catches%2A> ou uma atividade no bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> .|  
|<xref:System.Activities.Statements.TryCatch.Finally%2A>|False|A atividade a ser executada quando <xref:System.Activities.Statements.TryCatch.Try%2A> e todas as atividades necessárias na coleção de <xref:System.Activities.Statements.TryCatch.Catches%2A> tiver terminado a execução.<br /><br /> Você precisa pelo menos de adicionar uma atividade em <xref:System.Activities.Statements.TryCatch.Catches%2A> ou uma atividade no bloco de <xref:System.Activities.Statements.TryCatch.Finally%2A> .|  
  
## Consulte também  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [Rethrow](../workflow-designer/rethrow-activity-designer.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)