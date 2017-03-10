---
title: "Switch&lt;T&gt; Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.ModelItemKeyValuePair.UI"
  - "System.Activities.Statements.Switch`1.UI"
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
caps.latest.revision: 3
caps.handback.revision: 3
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Switch&lt;T&gt; Activity Designer
A atividade de <xref:System.Activities.Statements.Switch%601> avalia uma expressão especificada e executa a atividade de uma coleção de atividades cuja chave associado corresponde ao valor obtido de avaliação.  
  
 O **Switch \< T \>** designer de atividade é usado para criar e configurar um <xref:System.Activities.Statements.Switch%601> atividade a [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## A atividade Switch \< T \>  
 Uma atividade de <xref:System.Activities.Statements.Switch%601> contém <xref:System.Activities.Statements.Switch%601.Expression%2A> e um dicionário de <xref:System.Activities.Statements.Switch%601.Cases%2A>.  Cada caso o dicionário consiste em um par que contém *key* e uma atividade que serve como o *value*correspondente.  A atividade de <xref:System.Activities.Statements.Switch%601> avalia <xref:System.Activities.Statements.Switch%601.Expression%2A> e o compara com cada uma das chaves.  Se uma correspondência for encontrada, a atividade correspondente é executada.  Somente uma correspondência é possível porque as chaves de dicionário devem ser exclusivos de acordo com o tipo de igualdade definido pelo comparer de igualdade de dicionário.  Se nenhuma correspondência for encontrada, a atividade de <xref:System.Activities.Statements.Switch%601.Default%2A> é executada.  
  
## Como usar a opção \< T \> Designer de atividade  
 O **Switch \< T \>** designer de atividade pode ser encontrado no **fluxo de controle** categoria do **Toolbox**, que é acessada clicando o **Toolbox** guia o [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] \(como alternativa, selecione **barra de ferramentas** do **exibição** menu ou CTRL \+ ALT \+ X.\) Após solto no [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], ele exibe o **selecionar tipos** caixa de diálogo para permitir que o usuário especifique o tipo genérico *T* usados em <xref:System.Activities.Statements.Switch%601> atividade.  O valor padrão é **Int32**.  Quando o tipo genérico *T* foi selecionado, uma **Switch \< T \>** designer é adicionado ao designer de fluxo de trabalho.  
  
 Estas são as propriedades de **opção \< T \>** designer.  Todas essas propriedades podem ser editadas na grade de propriedade.  Alguns deless também podem ser editados na superfície de designer.  
  
 A tabela a seguir mostra as propriedades mais úteis de <xref:System.Activities.Statements.Switch%601> e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Switch%601> .  O valor padrão é Switch \< Int32 \>.  O valor pode ser editado na janela de **Propriedades** ou diretamente no cabeçalho de designer.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Especifica a expressão usada para comparar as chaves na coleção dos casos para determinar que casos a executar.|  
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Especifica a atividade executada se nenhuma correspondência for encontrada.  Clique no botão de **Adicionar uma atividade** no designer para abrir a caixa de **Padrão** onde a atividade pode ser descartada.|  
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Especifica os casos a ser avaliado.  Para adicionar um caso, clique o **adicionar novo caso** botão na parte inferior da **Switch \< T \>** designer.  O botão muda para uma caixa de texto \(caixa de combinação se o tipo genérico selecionado ao adicionar a opção \< T \> é a cadeia de caracteres ou Enum\).  Após adicionar uma chave na caixa de **Valor do caso** , a área dos casos expande e uma atividade pode ser descartada onde o texto “atividade de dica operação aqui” definir a lógica de execução para casos.|  
  
 Vários casos podem ser adicionados como as chaves dos casos não são duplicadas.  Se não, uma caixa de diálogo de erro exibe relatar a chave especificada dos casos já existe e que você deve escolher uma chave diferente.  No **Switch \< T \>** designer, apenas uma área dos casos pode estar na exibição expandida por vez.  Se uma área dos casos está na visualização recolhida, clique na área dos casos para expandi\-la.  Observe que para casos, recolhidos de designer mostra o nome para exibição de atividade dentro dos casos no lado direito se houver.  Se não, mostra o botão de **Adicionar uma atividade** que expande o caso se você clicar nos e permite que você adicione uma atividade.  
  
 Clique na chave de casos existentes altera a chave de um rótulo em uma caixa de texto para que você possa editar a chave dos casos.  
  
 Existem 2 maneiras de excluir casos:  
  
1.  Selecione os casos e excluir\-los.  
  
2.  Selecione os casos, clique com o botão direito do mouse para exibir o menu de contexto e selecione **Excluir**.  
  
 Observe que você deve selecionar os casos os próprios para excluir.  Selecionando e excluindo a atividade dentro de um caso exclui somente a atividade não os casos.  
  
## Consulte também  
 [Control Flow](../workflow-designer/control-flow-activity-designers.md)