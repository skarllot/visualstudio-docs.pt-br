---
title: "Using the Legacy Activity Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "activities, configuring"
  - "custom activities"
  - "Activity Designer"
  - "child activities, adding"
  - "activities, adding child"
  - "activities, creating custom"
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Using the Legacy Activity Designer
Este tópico descreve como usar o designer de atividade em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]herdado.  Use o designer herdado na definição [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 O designer de atividade permite que você crie suas próprias atividades personalizados.  
  
## Criando uma atividade personalizado  
 Siga estas etapas para criar uma atividade personalizado utilizando o designer de atividade:  
  
1.  No menu de **Projeto** , clique **Adicionar Atividade**.  
  
2.  Selecione o modelo de **Atividade** ou de **Atividade \(com separação de código\)** .  
  
    1.  Use o modelo de **Atividade** para criar uma atividade com a definição de atividade e o código do usuário no mesmo arquivo de código.  
  
    2.  Use o modelo de **Atividade \(com separação de código\)** para criar uma atividade com a definição de atividade expressa como a marcação de fluxo de trabalho e o código do usuário em um arquivo separado de código.  
  
3.  Digite um nome de atividade ou manter o nome padrão, e clique em **Adicionar**.  
  
 Você também pode criar um conjunto de atividades personalizados criando um novo projeto do tipo **Workflow Activity Library**.  Para obter mais informações sobre este tipo de projeto, consulte [How to: Create a Workflow Activity Library \(Legacy\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md).  
  
## Configurando uma atividade  
 Quando o designer de atividade estiver ativo, você pode usar o navegador de propriedade para configurar as propriedades listadas na tabela a seguir.  
  
|Propriedade|Comentários|  
|-----------------|-----------------|  
|**Name**|Nome da atividade.|  
|**Base Class**|Classe base que a atividade deriva.  A classe base padrão é [SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020).  Na janela **Propriedades**, clique nas reticências **\[…\]** de **Classe Base** para selecionar outra classe base em [Browse and Select a .NET Type Dialog Box \(Legacy\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|  
|**Description**|Descrição definido pelo usuário de atividade.|  
|**Enabled**|Defina a **True** por padrão para ativar a execução e validação de atividade.  Defina a **False** para desativar a execução e validação de atividade.  Para obter informações sobre validação e execução de atividade, consulte [atividades de fluxo de trabalho de desenvolvimento](http://go.microsoft.com/fwlink?LinkID=65024).|  
  
## Adicionando atividades filhos  
 Você pode arrastar atividades filhos da caixa de ferramentas para a atividade que você está criando.  Você pode então configurar cada atividade filho usando o navegador de propriedade.  
  
## Consulte também  
 [Desenvolver as atividades de fluxo de trabalho](http://go.microsoft.com/fwlink?LinkID=65024)   
 [Criação de atividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65021)   
 [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)   
 [Exemplos de atividades personalizadas](http://go.microsoft.com/fwlink?LinkID=65022)   
 [How to: Create a Workflow Activity Library \(Legacy\)](../Topic/How%20to:%20Create%20a%20Workflow%20Activity%20Library%20\(Legacy\).md)   
 [Using the Legacy Workflow Designer](../workflow-designer/using-the-legacy-workflow-designer.md)