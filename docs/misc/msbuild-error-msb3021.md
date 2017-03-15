---
title: "Erro MSB3021 (MSBuild) | Microsoft Docs"
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
  - "MSBuild.Copy.Error"
helpviewer_keywords: 
  - "MSB3021"
ms.assetid: 8cb3a860-6916-4406-b5c7-b1106b44b92a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erro MSB3021 (MSBuild)
**Não é possível copiar o arquivo "' \< arquivo \>'" arquivo "' \< arquivo \>'". '\< erro \>'**  
  
 O `Copy` tarefa não é possível copiar o arquivo especificado.  
  
### Para corrigir este erro  
  
-   Verifique se o arquivo de destino está bloqueado \(em uso\) por outro aplicativo. Certifique\-se de que você tem permissão para ler o arquivo de origem e gravar o arquivo de destino para a pasta de destino. Se o caminho do arquivo de destino for muito longo, você talvez precise copiar para um local diferente.  
  
## Consulte também  
 [Tarefa Copy](../msbuild/copy-task.md)   
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)