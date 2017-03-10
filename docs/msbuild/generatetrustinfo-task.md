---
title: "Tarefa GenerateTrustInfo | Microsoft Docs"
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
helpviewer_keywords: 
  - "Tarefa GenerateTrustInfo [MSBuild]"
  - "MSBuild, Tarefa GenerateTrustInfo"
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GenerateTrustInfo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gera a confiança do aplicativo a partir do manifesto de base e o `TargetZone` e `ExcludedPermissions` parâmetros.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `GenerateTrustInfo` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`ApplicationDependencies`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os assemblies dependentes.|  
|`BaseManifest`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o manifesto de base para gerar a relação de confiança do aplicativo.|  
|`ExcludedPermissions`|Opcional `String` parâmetro.<br /><br /> Especifica um ou mais valores de identidade de permissão separada por ponto\-e\-vírgula a serem excluídos do conjunto de permissões padrão de zona.|  
|`TargetZone`|Opcional `String` parâmetro.<br /><br /> Especifica um conjunto de permissões padrão de zona, que é obtido a partir da diretiva de máquina.|  
|`TrustInfoFile`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem> parâmetro de saída.<br /><br /> Especifica o arquivo que contém as informações de confiança de segurança do aplicativo.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)