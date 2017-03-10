---
title: "Tarefa GetReferenceAssemblyPaths | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 178ef49c-5dee-405b-a14b-a37f41dc0609
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GetReferenceAssemblyPaths
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Retorna a referência de caminhos de assembly de vários frameworks.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `GetReferenceAssemblyPaths` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`ReferenceAssemblyPaths`|Opcional `String[]` parâmetro de saída.<br /><br /> Retorna o caminho, com base na `TargetFrameworkMoniker` parâmetro.  Se a `TargetFrameworkMoniker` é nulo ou vazio, esse caminho será `String.Empty`.|  
|`FullFrameworkReferenceAssemblyPaths`|Opcional `String[]` parâmetro de saída.<br /><br /> Retorna o caminho, com base na `TargetFrameworkMoniker` parâmetro, sem considerar a parte de perfil do moniker.  Se a `TargetFrameworkMoniker` é nulo ou vazio, esse caminho será `String.Empty`.|  
|`TargetFrameworkMoniker`|Opcional `String` parâmetro.<br /><br /> Especifica o identificador de origem de framework de destino que está associado com os caminhos de referência de assembly.|  
|`RootPath`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho de raiz usar para gerar o caminho do assembly de referência.|  
|`BypassFrameworkInstallChecks`|Opcional [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) parâmetro.<br /><br /> Se `true`, ignora as verificações básicas que `GetReferenceAssemblyPaths` executa por padrão para garantir que determinadas estruturas de tempo de execução são instaladas, dependendo da estrutura de destino.|  
|`TargetFrameworkMonikerDisplayName`|Opcional `String` parâmetro de saída.<br /><br /> Especifica o nome de exibição para o moniker do framework de destino.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)