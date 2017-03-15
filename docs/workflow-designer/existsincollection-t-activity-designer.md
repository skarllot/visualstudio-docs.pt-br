---
title: "ExistsInCollection&lt;T&gt; Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.ExistsInCollection`1.UI"
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# ExistsInCollection&lt;T&gt; Activity Designer
O **ExistsInCollection \< T \>** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.ExistsInCollection%601> atividade.  
  
## A atividade de Existsincollectiont \< T \>  
 A atividade de <xref:System.Activities.Statements.ExistsInCollection%601> determina se um item específico existe em uma coleção específico.  
  
### Usando o Designer de atividade de Existsincollectiont \< T \>  
 O **ExistsInCollection \< T \>** designer de atividade pode ser encontrado no **coleção** categoria do **Toolbox**, que é acessada clicando o **Toolbox** guia de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL \+ ALT \+ X.\)  
  
 O **ExistsInCollection \< T \>** designer de atividade pode ser arrastado do **Toolbox** e ser solto sobre a [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] superfície onde quer que as atividades são colocadas em geral, como em um <xref:System.Activities.Statements.Sequence>.  Isso cria uma <xref:System.Activities.Statements.ExistsInCollection%601> atividade com um padrão <xref:System.Activities.Activity.DisplayName%2A> de Existsincollectionint32 \< Int32 \>.  \(Por padrão, *TypeArgument* é **Int32**.  Pode ser alterado na grade de propriedade.\)  O <xref:System.Activities.Activity.DisplayName%2A> valor pode ser editado no cabeçalho do **ExistsInCollection \< T \>** designer de atividade ou no **DisplayName** caixa da grade de propriedade.  Outras propriedades devem ser editadas na grade de propriedade.  
  
### As propriedades de Existsincollectiont \< T \>  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.ExistsInCollection%601> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|O nome amigável de atividade de <xref:System.Activities.Statements.ExistsInCollection%601> .  O padrão é Existsincollectionint32 \< Int32 \>.  Embora o valor de <xref:System.Activities.Activity.DisplayName%2A> não é necessário restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|Item a ser adicionado à coleção \< T \>.  Este item é do tipo *T* é do tipo *TypeArgument*.  Para especificar o item, digite uma expressão do Visual Basic na grade de propriedade.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|A coleção para que o item deve ser adicionado.  Essa coleção é do tipo **ICollection\<TypeArgument\>.** para especificar a coleção, digite uma expressão do Visual Basic na grade de propriedade.|  
|*TypeArgument*|True|O tipo T de itens contidos em <xref:System.Collections.Generic.ICollection%601>.  Por padrão, esse tipo de *TypeArgument* é definido como **Int32**.  Para alterar o tipo, altere o valor de *TypeArgument* na caixa de combinação na grade de propriedade.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|Um valor que indica se o item especificado existe na coleção.  Para especificar uma variável para associar ao resultado, digite uma variável do Visual Basic na grade de propriedade.|  
  
## Consulte também  
 [Collection](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T\>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T\>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T\>](../workflow-designer/removefromcollection-t-activity-designer.md)