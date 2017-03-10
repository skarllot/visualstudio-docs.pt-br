---
title: "Erro MSB3071 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.Exec.AllDriveLettersMappedError"
helpviewer_keywords: 
  - "MSB3071"
ms.assetid: 8afbc6ec-e399-4f06-a30b-f33c87642ef7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3071 (MSBuild)
**Todas as letras de unidade de r: a z: estão em uso no momento. Como o diretório de trabalho "' \< caminho \>'" é um caminho UNC, a tarefa "Exec" precisa de uma letra de unidade livre para mapear o caminho UNC. Desconectar de um ou mais recursos compartilhados para liberar letras de unidade ou especifique um diretório de trabalho local antes de tentar este comando novamente.**  
  
 Todas as letras de unidade da: a z estão atualmente em uso. Como o diretório de trabalho especificado é um caminho UNC, o `Exec` tarefa precisa de uma letra de unidade livre para a qual mapear o caminho UNC.  
  
### Para corrigir este erro  
  
-   Desconectar de um ou mais recursos compartilhados para liberar letras de unidade  
  
-   Especifique um diretório de trabalho local antes de tentar este comando novamente.  
  
## Consulte também  
 [Tarefa Exec](../msbuild/exec-task.md)