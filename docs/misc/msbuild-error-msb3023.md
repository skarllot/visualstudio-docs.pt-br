---
title: "Erro MSB3023 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.Copy.NeedsDestination"
helpviewer_keywords: 
  - "MSB3023"
ms.assetid: 3505ad1e-d54f-4cb4-a299-ac03684cb391
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3023 (MSBuild)
**Nenhum destino especificado para a cópia. Forneça o "'\< attribute \>'" ou "' \< attribute \>'".**  
  
 Um destino deve ser especificado para o `Copy` tarefa usando um dos atributos de tarefa `DestinationFiles`e`DestinationDirectory`.  
  
### Para corrigir este erro  
  
-   Especifique o `DestinationFiles`ou`DestinationDirectory`para o `Copy` tarefa.  
  
## Consulte também  
 [Tarefa Copy](../msbuild/copy-task.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)