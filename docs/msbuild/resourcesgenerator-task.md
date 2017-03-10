---
title: "Tarefa ResourcesGenerator | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "inserindo recursos em um arquivo .resources [WPF MSBuild]"
  - "Tarefa ResourcesGenerator [WPF MSBuild]"
  - "Tarefa ResourcesGenerator [WPF MSBuild], parâmetros"
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa ResourcesGenerator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> tarefa incorpora um ou mais recursos \(. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] em formato binário e outros tipos de extensão\) em um arquivo. Resources.  
  
## Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`OutputPath`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o caminho do diretório de saída.  Se o caminho não é um caminho absoluto, ele é tratado como um caminho relativo ao diretório raiz do projeto.|  
|`OutputResourcesFile`|Obrigatório  **\[\] de ITaskItem** parâmetro de saída.<br /><br /> Especifica o caminho e o nome do arquivo. resources gerado.  Se o caminho não é um caminho absoluto, o arquivo. Resources é gerado em relação ao diretório raiz do projeto.|  
|`ResourcesFiles`|Obrigatório  **\[\] de ITaskItem** parâmetro.<br /><br /> Especifica um ou mais recursos para incorporar no arquivo. resources gerado.|  
  
## Exemplo  
 O exemplo a seguir gera um arquivo. Resources com um recurso único bmp.  O recurso. bmp é gerado para um diretório que é relativo ao diretório raiz do projeto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="ResourcesGeneratorTask">  
    <ResourcesGenerator  
      ResourceFiles="Resource1.bmp"  
      OutputPath="myresources"  
      OutputResourcesFile="myresources\my.resources" />  
  </Target>  
</Project>  
```  
  
## Consulte também  
 [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)