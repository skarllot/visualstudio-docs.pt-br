---
title: "Erro MSB3072 (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.Exec.MissingCommandError"
helpviewer_keywords: 
  - "MSB3072"
ms.assetid: c8468e1c-d8c7-441c-b274-123ac856f147
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3072 (MSBuild)
**A tarefa "Exec" precisa de um comando seja executado.**  
  
 O atributo `Command` é um atributo necessário para o `Exec` tarefa.  
  
### Para corrigir este erro  
  
1.  No arquivo de projeto, especifique o atributo `Command` para o `Exec` tarefa.  
  
## Consulte também  
 [Tarefa Exec](../msbuild/exec-task.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)