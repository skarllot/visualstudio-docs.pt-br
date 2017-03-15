---
title: "How to: Debug XAML with the Workflow Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
caps.latest.revision: 8
caps.handback.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# How to: Debug XAML with the Workflow Designer
Fluxos de trabalho são definidos em termos de XAML.  A representação de interface de usuário de fluxo de trabalho é construída sobre a árvore XAML que define o fluxo de trabalho.  A experiência de depuração é semelhante a depuração fluxos de trabalho em [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  Por exemplo, ao depurar XAML, os locais, a observação, e o trabalho das janelas de segmentos da mesma maneira que faz sobre depuração de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] .  Além disso, a exibição da pilha de chamadas durante a depuração XAML é uma exibição hierárquica linha com base de fluxo de execução do fluxo de trabalho.  
  
> [!NOTE]
>  Se o XAML para um fluxo de trabalho está localizado no mesmo assembly que as atividades, a parte do assembly de nomes de classe não é incluído.  Sem esta parte dos nomes de classe \(atividade\), o XAML não pode ser carregado no tempo de execução.  Não é recomendável definir atividades no mesmo namespace que o projeto pai; caso contrário, o XAML deverá mão\- ser editado após ser editado no designer.  
  
### Para depurar o fluxo de trabalho XAML  
  
1.  Abrir um projeto de fluxo de trabalho ou de atividade em [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Definir um ponto de interrupção na atividade ou nas atividades que você deseja depurar como descrito em [How to: Set Breakpoints in Workflows](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md).  
  
3.  Clique com o botão direito do mouse no arquivo .xaml que contém seus definição de fluxo de trabalho e **Exibir Código**.  Você verá um ponto de interrupção exibido na mesma linha da declaração de elemento XAML de atividade que você definir o ponto de interrupção sobre no modo design.  
  
4.  Chamar o depurador como descrito em [How to: Invoke the Workflow Debugger](../workflow-designer/how-to-invoke-the-workflow-debugger.md).  
  
5.  Quando a execução de código atinge um de seus pontos de interrupção, o elemento XAML associado com esse ponto de interrupção será realçado.  Para mover o ponto de interrupção seguir, use a chave de **F10** ou de **F11** .  
  
## Consulte também  
 [How to: Set Breakpoints in Workflows](../Topic/How%20to:%20Set%20Breakpoints%20in%20Workflows.md)   
 [How to: Invoke the Workflow Debugger](../workflow-designer/how-to-invoke-the-workflow-debugger.md)