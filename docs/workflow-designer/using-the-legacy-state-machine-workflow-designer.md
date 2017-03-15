---
title: "Using the Legacy State Machine Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "StateFinalizationActivity activity"
  - "StateActivity activity"
  - "SetStateActivity activity"
  - "EventDrivenActivity activity"
  - "state machine workflow designer"
  - "state machine workflows, designer"
  - "state machine workflows, activities"
  - "StateInitializationActivity activity"
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Using the Legacy State Machine Workflow Designer
Quando você estiver criando um novo projeto de fluxo de trabalho do computador de estado em [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] que tem como alvo [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], você pode escolher usar **Aplicativo de console do fluxo de trabalho do computador de estado** ou herdado o modelo de projeto de **Biblioteca de fluxo de trabalho do computador de estado** .  Se você escolher um desses modelos de projeto do computador de estado, o designer do computador de estado é apresentado como a interface do usuário herdado do designer de fluxo de trabalho.  Para obter informações sobre modelos de projeto herdados do computador de estado, consulte [How to: Create State Machine Workflow Console Applications \(Legacy\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md) e [How to: Create a State Machine Workflow Library \(Legacy\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md).  
  
 Um fluxo de trabalho do computador de estado consiste em um conjunto de estados.  Um estado denotado é como um estado inicial.  Cada estado pode receber um determinado conjunto de eventos.  Baseado em um evento, uma transição pode ser feita para outro estado.  O fluxo de trabalho do computador de estado pode ter um estado final.  Quando uma transição é feita ao estado final, o fluxo de trabalho completa.  
  
## Modos de exibição do designer do computador de estado  
 O designer do computador de estado é um designer de forma livre, o que significa que as atividades podem ser movidos para o redor livremente na superfície de design.  O designer do computador de estado tem dois modos: o modo *de estado* e exibição *de baseada* .  
  
 Modo de estado mostra as atividades de estado e as atividades corretamente eventos que podem ser contidas dentro de uma atividade de estado.  Nesta exibição, as transições de um estado para outro são representadas por linhas que estendem de atividade de baseada em um estado para outro estado.  Você também pode criar transições desenhando a linha você mesmo.  Para desenhar a transição, selecione a atividade de baseada e em seguida, selecione uma das alças da atividade e arraste\-a.  Esta ação desenha uma linha.  Esta linha é anexada no estado de destino, indicando uma transição entre estados.  
  
 Para acessar a exibição orientada evento, clique duas vezes em uma atividade de baseada.  O designer que aparece é bem como o designer sequencial de fluxo de trabalho.  Na parte superior do designer, uma barra de navegação mostra a hierarquia de atividades até a atividade de baseada que é exibida.  Você pode navegar de volta para o modo de estado clicando em qualquer elemento na hierarquia exibida.  Se você desenhou uma transição de um estado para outro no modo de estado, e se você está exibindo a exibição orientada a eventos da atividade, uma atividade do estado é adicionada à atividade de baseada para você.  Se você alterar as propriedades de atividade do estado, é passado refletida no modo de estado.  
  
## Atividades de fluxo de trabalho do computador de estado  
 A tabela a seguir descreve as atividades principais que são usadas em um designer de fluxo de trabalho do computador de estado.  
  
|Nome da caixa de ferramentas|Atividade|Descrição|  
|----------------------------------|---------------|---------------|  
|**Estado**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Representa um estado em um computador de estado; pode conter atividades adicionais de **StateActivity** .  Para obter mais informações, consulte [usando a atividade de StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Especifica uma transição para um novo estado.  Para obter mais informações, consulte [usando a atividade de SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Executa quando um estado estiver conectado; pode conter outras atividades.  Para obter mais informações, consulte [usando a atividade de StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Executa atividades contidas ao sair de um [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) atividade.  Para obter mais informações, consulte [usando a atividade de StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Usado para os estados que contam com um evento externa para iniciar executar.  O **EventDrivenActivity** atividade deve ter uma atividade que implementa o [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) interface como a primeira atividade filho.  Para obter mais informações, consulte [usando a atividade de EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 O componente principal em um fluxo de trabalho de máquina de estado é o [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) atividade.  Como os eventos são capturados em vários pontos em um fluxo de trabalho do computador de estado, os estados diferentes estão conectados para manipular as tarefas associadas com eventos.  Durante o tempo de vida de fluxo de trabalho, o fluxo de trabalho pode sair e inserir vários estados diferentes.  Esses estados conectam uns aos outros usando o [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) atividade.  
  
 Quando você arrasta um novo **StateActivity** na superfície de design de fluxo de trabalho, você pode adicionar [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), ou adicional **StateActivity** atividades como atividades filho.  
  
> [!CAUTION]
>  Quando você usa o designer de fluxo de trabalho do computador de estado para criar fluxos de trabalho, você deve monitorar a estrutura de fluxo de trabalho que você está criando com a janela de exibição de **Estrutura de Tópicos de Documento** .  A exibição da estrutura de fluxo de trabalho do computador de estado na janela de exibição de **Estrutura de Tópicos de Documento** espelha o layout lógico de atividades no arquivo de marcação de fluxo de trabalho.  O layout físico das atividades de fluxo de trabalho como aparecem na superfície de design não pode espelhar o layout lógico de atividades no arquivo de marcação de fluxo de trabalho.  
>   
>  Para abrir a janela de **Estrutura de Tópicos de Documento** , no menu de **Modo de Visualização** , aponte para **Outras Janelas**, selecione **Estrutura de Tópicos de Documento**.  
  
## Consulte também  
 [How to: Create State Machine Workflow Console Applications \(Legacy\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md)   
 [How to: Create a State Machine Workflow Library \(Legacy\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md)   
 [Fluxos de trabalho de máquina de estado](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Usando a atividade de StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Usando a atividade de StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Usando a atividade de StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Usando a atividade de SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Usando a atividade de EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)