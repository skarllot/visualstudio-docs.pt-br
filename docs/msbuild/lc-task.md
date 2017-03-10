---
title: "Tarefa LC | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "tarefa LC [MSBuild]"
  - "MSBuild, tarefa LC"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa LC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quebra o LC.exe, que gera um arquivo de .license de um arquivo. licx.  Para obter mais informações sobre LC.exe, consulte [Lc.exe \(Compilador de Licença\)](../Topic/Lc.exe%20\(License%20Compiler\).md).  
  
## Parâmetros  
 A tabela a seguir descreve os parâmetros para o `LC` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`LicenseTarget`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem> parâmetro.<br /><br /> Especifica o executável para o qual os arquivos de .licenses são gerados.|  
|`NoLogo`|Opcional `Boolean` parâmetro.<br /><br /> Suprime a exibição Microsoft faixa de inicialização.|  
|`OutputDirectory`|Opcional `String` parâmetro.<br /><br /> Especifica o diretório no qual colocar os arquivos de .licenses de saída.|  
|`OutputLicense`|Opcional <xref:Microsoft.Build.Framework.ITaskItem> parâmetro de saída.<br /><br /> Especifica o nome do arquivo .licenses.  Se você não especificar um nome, o nome do arquivo. licx é usado e o arquivo .licenses é colocado no diretório que contém o arquivo. licx.|  
|`ReferencedAssemblies`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os componentes referenciados para carregar quando gerar o arquivo .license.|  
|`SdkToolsPath`|Opcional `String` parâmetro.<br /><br /> Especifica o caminho para as ferramentas do SDK, como, por exemplo, Resgen. exe.|  
|`Sources`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os itens que contenham componentes licenciados para incluir no arquivo .licenses.  Para obter mais informações, consulte a documentação para o `/complist` alternar no [Lc.exe \(Compilador de Licença\)](../Topic/Lc.exe%20\(License%20Compiler\).md).|  
  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.ToolTaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.ToolTask> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe ToolTaskExtension \(base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir usa a `LC` tarefa para compilar as licenças.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)