---
title: "Transition Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Transition.UI"
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "sdanie"
manager: "erikre"
---
# Transition Activity Designer
<xref:System.Activities.Statements.Transition> representa a transição entre dois estados.  
  
## Usando o designer de atividade de transição  
 O designer de atividade de transição permite que você configure uma transição entre dois estados.  
  
### Propriedades de transição em Designer de Fluxo de Trabalho  
 A tabela a seguir mostra as propriedades de <xref:System.Activities.Statements.Transition> que podem ser definidas usando o designer de fluxo de trabalho e descreve como elas são usadas no designer.  
  
|Nome da propriedade|Obrigatório|Uso|  
|-------------------------|-----------------|---------|  
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|False|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Transition> .  O valor padrão é **T1**.  O valor pode ser editado na grade de propriedade, no cabeçalho de designer expandido de transição, e o cabeçalho da seção de ação dentro do designer expandido de transição.  <xref:System.Activities.Activity.DisplayName%2A> é usado em navegação de rastreamento que é exibida na parte superior do designer de fluxo de trabalho.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|  
|<xref:System.Activities.Statements.Transition.Condition%2A>|False|Se o presente, especifica uma expressão que deve ser avaliada como **True** antes que o controle é passado para o estado de destino.  Essa condição pode ser editada na grade de propriedade e expandido no designer de transição.  Várias condições em uma transição compartilhado são avaliadas na ordem em que aparecem no designer de transição. **Note:**  Observe que se <xref:System.Activities.Statements.Transition.Condition%2A> de uma transição for avaliada como **False** \(ou todas as condições de uma transição do gatilho compartilhada for avaliada como **False**\), a transição não ocorrerá e todos os gatilhos para todas as transições de estado serão reprogramados.  Neste tutorial, essa situação não pode ocorrer devido à maneira como as condições são configuradas \(temos ações específicas para se o palpite está correto ou incorreto\).|  
|**Origem**|True|Indica o estado de que essa transição se origina.  Clicando no nome do estado de origem alterna a exibição do designer para uma exibição expandida de estado.  Esse valor é definido quando a transição é criada e não pode ser alterada.|  
|<xref:System.Activities.Statements.Transition.Trigger%2A>|False|Especifica a atividade cuja conclusão inicia a transição.  Para definir esta atividade, arraste uma atividade de **Caixa de Ferramentas** e soltar\-la na seção de **Disparador** de transição.|  
|<xref:System.Activities.Statements.Transition.Action%2A>|False|Especifica a atividade que é executada quando a atividade do disparador concluiu e <xref:System.Activities.Statements.Transition.Condition%2A>, se presentes, ele avalia a **true**.  Esta atividade é executada ao fazer a transição para estado de destino, após a atividade de <xref:System.Activities.Statements.State.Exit%2A> para o estado de origem, se presentes, é executada.  Quando o designer de transição é expandido, esse valor pode ser definido arrastar uma atividade de **Caixa de Ferramentas** e soltando\-os à seção de **Ação** de transição.  Pode haver várias ações para uma única transição.  As ações individuais podem ser expandidos e reduzido, e podem ser classificadas clicando para cima ou para baixo a seta que aparece em ação quando há várias ações em uma transição.|  
|**Destino**|True|Indica o estado que as transições do computador de estado após a transição concluírem.  Isso corresponde à propriedade de <xref:System.Activities.Statements.Transition.To%2A> de transição no modelo de objeto.  Clicando no nome do estado de destino alterna a exibição do designer para uma exibição expandida de estado.  Esse valor é definido quando a transição é criada e pode ser modificada arrastando a seta que se conecta a transição para estado de destino no designer.|  
  
### Criar transições  
 As transições são criados arrastando uma linha de um estado para outro, ou soltando um estado em triângulos que aparecem quando um estado é arrastado sobre outro estado.  Para criar uma transição, arrastando passa o mouse sobre a borda do estado de origem, e arraste uma linha de estado da fonte para o estado de destino.  Para criar uma transição soltando\-se, arraste o estado de destino e focalizar\-lo sobre o estado de origem, e solte\-o em um dos quatro triângulos que aparecem em torno do estado de exibição source.  O estado de destino pode ser um novo estado arrastado de **Caixa de Ferramentas**, ou um estado existente arrastado de designer de fluxo de trabalho.  
  
> [!NOTE]
>  Um único estado em um computador de estado pode ter até 76 transições criadas utilizando o designer de fluxo de trabalho.  O limite nas transições para um estado para fluxos de trabalho criados fora de designer é delimitado somente por recursos do sistema.  
  
 As transições compartilhadas do disparador são o conjunto de transições que compartilham o mesmo evento do disparador.  Um disparador compartilhado permite a progressão condicional a um estado de destino com base na classificação de expressões configuradas para várias transições que compartilham um evento comuns de disparador.  Para adicionar ações adicionais para uma transição e criar uma transição compartilhada, clique no círculo que indica o início de transição desejada e arraste\-o para estado desejado.  A nova transição compartilhar um disparador mesmo que a transição inicial, mas terá uma condição e uma ação exclusivos.  As transições compartilhadas também podem ser criadas de dentro do designer de transição clicando em **Adicionar transição de gatilho compartilhado** na parte inferior do designer de transição, e selecionando o estado desejado de destino no menu suspenso **Estados disponíveis para conexão**.  
  
## Consulte também  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [State](../workflow-designer/state-activity-designer.md)