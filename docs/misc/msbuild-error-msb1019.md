---
title: "Erro MSB1019 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.InvalidLoggerError"
helpviewer_keywords: 
  - "MSB1019"
ms.assetid: 5d0169f7-f878-433a-ac30-d9d6010130af
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB1019 (MSBuild)
**Opção de agente de log não foi construída corretamente.**  
  
 O **\/logger** chave não for especificada corretamente. Para especificar um agente de log, você deve fornecer pelo menos o assembly ou se você quiser ser explicitamente especifique qual carregar, forneça a classe logger e o assembly do registrador. Parâmetros de agente são opcionais.  
  
### Para corrigir este erro  
  
1.  Especifique um agente de log usando a classe logger e o assembly do agente de log. O `<logger>` sintaxe é:  
  
     `<logger class>,<logger assembly>[;<logger parameters>]`  
  
     O `<logger class>` sintaxe é:  
  
    ```  
    [<partial or full namespace>.]<logger class name>  
    ```  
  
     O `<logger assembly>`sintaxe é:  
  
    ```  
    {<assembly name>[,<strong name>] | <assembly file>}  
    ```  
  
     O `<logger parameters>` são opcionais e são passados ao agente de log exatamente como você os digitou.  
  
     Exemplo: \/`logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`  
  
## Consulte também  
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)   
 [Agentes de log de compilação](../msbuild/build-loggers.md)