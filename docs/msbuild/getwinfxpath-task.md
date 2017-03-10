---
title: "Tarefa GetWinFXPath | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "obtendo o diretório do tempo de execução do .NET Framework atual [WPF MSBuild]"
  - "Tarefa GetWinFXPath [WPF MSBuild]"
  - "Tarefa GetWinFXPath [WPF MSBuild], parâmetros"
  - "obtendo o caminho para o do tempo de execução do .NET Framework atual [WPF MSBuild]"
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GetWinFXPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

O <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> tarefa retorna o diretório do atual [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] em tempo de execução.  
  
## Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`WinFXPath`|Opcional  **seqüência de caracteres** parâmetro de saída.<br /><br /> Especifica o caminho real para o [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)] em tempo de execução.|  
|`WinFXNativePath`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o caminho para o nativo [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] em tempo de execução.|  
|`WinFXWowPath`|Obrigatório  **seqüência de caracteres** parâmetro.<br /><br /> Especifica o caminho para o [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] assemblies em 32 bits  **Windows on Windows** o módulo em sistemas de 64 bits.|  
  
## Comentários  
 Se a <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> tarefa está em execução em um processador de 64 bits, o  **WinFXPath** parâmetro for definido como o caminho que é armazenado na  **WinFXWowPath** parâmetro; Caso contrário, o  **WinFXPath** parâmetro for definido como o caminho que é armazenado na  **WinFXNativePath** parâmetro.  
  
## Exemplo  
 O exemplo a seguir mostra como usar o  **GetWinFXPath** tarefas para detectar o caminho nativo para o [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] em tempo de execução.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.GetWinFXPath"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GetWinFXPathTask">  
    <GetWinFXPath  
      WinFXNativePath="c:\WinFXNative"   
      WinFXWowPath="c:\WinFXWowNative" />  
  </Target>  
  <Import Project="$(MSBuildBinPath)\Microsoft.WinFX.targets" />  
</Project>  
```  
  
## Consulte também  
 [Referência do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)