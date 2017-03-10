---
title: "Tarefa RequiresFramework35SP1Assembly | Microsoft Docs"
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
  - "MSBuild, Tarefa RequiresFramework35SP1Assembly"
  - "Tarefa RequiresFramework35SP1Assembly [MSBuild]"
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa RequiresFramework35SP1Assembly
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Determina se o aplicativo requer o.NET Framework 3.5 SP1.  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros da `RequiresFramework35SP1Assembly` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Assemblies`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os assemblies referenciados no aplicativo.|  
|`CreateDesktopShortcut`|Opcional `Boolean` parâmetro.<br /><br /> Se `true`, cria um ícone de atalho na área de trabalho durante a instalação.|  
|`DeploymentManifestEntryPoint`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o nome do arquivo de manifesto do aplicativo.|  
|`EntryPoint`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o assembly que deve ser executado quando o aplicativo é executado.|  
|`ErrorReportUrl`|Opcional `String` parâmetro.<br /><br /> Especifica o site da Web que é exibido nas caixas de diálogo que são encontradas durante as instalações de ClickOnce.|  
|`Files`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica a lista de arquivos que serão implantados quando o aplicativo é publicado.|  
|`ReferencedAssemblies`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os assemblies referenciados no projeto.|  
|`RequiresMinimumFramework35SP1`|Opcional `Boolean` parâmetro de saída.<br /><br /> Se `true`, o aplicativo requer o.NET Framework 3.5 SP1.|  
|`SigningManifests`|Opcional `Boolean` parâmetro de saída.<br /><br /> Se `true`, os manifestos de ClickOnce são assinados.|  
|`SuiteName`|Opcional `String` parâmetro.<br /><br /> Especifica o nome da pasta no  **Iniciar** menu no qual o aplicativo será instalado.|  
|`TargetFrameworkVersion`|Opcional `String` parâmetro.<br /><br /> Especifica a versão do.NET Framework que esta destinos do aplicativo.|  
  
## Comentários  
 Para além de ter os parâmetros listados na tabela, essa tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)