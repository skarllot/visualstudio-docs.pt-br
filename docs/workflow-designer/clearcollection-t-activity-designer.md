---
title: "ClearCollection&lt;T&gt; Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ClearCollection`1.UI"
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ClearCollection&lt;T&gt; Activity Designer
O **ClearCollection \< T \>** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.ClearCollection%601> atividade.  
  
## A atividade de Clearcollectiont \< T \>  
 A atividade de <xref:System.Activities.Statements.ClearCollection%601> limpa especificada uma coleção de todos os itens.  
  
### Usando o Designer de atividade de Clearcollectiont \< T \>  
 O **ClearCollection \< T \>** designer de atividade pode ser encontrado no **coleção** categoria do **Toolbox**, que é acessada clicando o **Toolbox** guia do [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL \+ ALT \+ X.\)  
  
 O **ClearCollection \< T \>** designer de atividade pode ser arrastado do **Toolbox** e ser solto sobre a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades são colocadas em geral, como em um <xref:System.Activities.Statements.Sequence>.  Isso cria uma <xref:System.Activities.Statements.ClearCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de Clearcollectionint32 \< Int32 \>.  \(Por padrão, *TypeArgument* é **Int32**.  Isso pode ser alterado na grade de propriedade.\) O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **ClearCollection \< T \>** designer de atividade ou no **DisplayName** caixa da grade de propriedade.  Outras propriedades devem ser editadas na grade de propriedade.  
  
### As propriedades de Clearcollectiont \< T \>  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.ClearCollection%601> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável opcional de atividade de <xref:System.Activities.Statements.ClearCollection%601> .  O padrão é Clearcollectionint32 \< Int32 \>.  Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|Especifica a coleção a ser limpa os itens.  Essa coleção é do tipo **ICollection\<TypeArgument\>.** para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|  
|*TypeArgument*|True|Especifica o tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>.  Por padrão, esse tipo de *TypeArgument* é definido como **Int32**.  Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedade.|  
  
## Consulte também  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T\>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)