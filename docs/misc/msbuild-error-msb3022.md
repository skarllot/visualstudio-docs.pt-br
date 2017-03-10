---
title: "Erro MSB3022 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.Copy.ExactlyOneTypeOfDestination"
helpviewer_keywords: 
  - "MSB3022"
ms.assetid: 74ebcced-8a56-4502-8fef-43d36c79a640
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3022 (MSBuild)
**Ambos os "'\< attribute \>'" e "' \< atributo \>'" foram especificado como parâmetros de entrada no arquivo de projeto. Escolha um ou outro.**  
  
 Para o `Copy` tarefa, você deve especificar `DestinationFiles` ou `DestinationDirectory`,mas não os dois atributos de tarefa.  
  
### Para corrigir este erro  
  
-   Especifique o `DestinationFiles` ou `DestinationDirectory` para o `Copy` tarefa no arquivo de projeto.  
  
## Consulte também  
 [Tarefa Copy](../msbuild/copy-task.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)