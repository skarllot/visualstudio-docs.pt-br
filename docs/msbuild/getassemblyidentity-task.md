---
title: "Tarefa GetAssemblyIdentity | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetAssemblyIdentity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Tarefa GetAssemblyIdentity [MSBuild]"
  - "MSBuild, Tarefa GetAssemblyIdentity"
ms.assetid: a977e072-37ad-4941-84a6-32a4483be55d
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Tarefa GetAssemblyIdentity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recupera as identidades do conjunto de arquivos especificados e as informações de identidade de saídas.  
  
## Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da `GetAssemblyIdentity` tarefa.  
  
|Parâmetro|Descrição|  
|---------------|---------------|  
|`Assemblies`|Opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro de saída.<br /><br /> Contém as identidades recuperados do assembly.|  
|`AssemblyFiles`|Obrigatório <xref:Microsoft.Build.Framework.ITaskItem>`[]` parâmetro.<br /><br /> Especifica os arquivos para recuperar as identidades de.|  
  
## Comentários  
 Os itens de saída o `Assemblies` parâmetro contém entradas de metadados de item chamadas `Version`, `PublicKeyToken`, e `Culture`.  
  
 Com os parâmetros listados acima, esta tarefa herda os parâmetros da <xref:Microsoft.Build.Tasks.TaskExtension> herda de classe, que por si só a <xref:Microsoft.Build.Utilities.Task> classe.  Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe TaskExtension \(base\)](../msbuild/taskextension-base-class.md).  
  
## Exemplo  
 O exemplo a seguir recupera a identidade dos arquivos especificados na `MyAssemblies` do item e envia\-los para o `MyAssemblyIdentities` item.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyAssemblies Include="File1.dll;File2.dll" />  
    </ItemGroup>  
  
    <Target Name="RetrieveIdentities>  
        <GetAssemblyIdentity  
            AssemblyFiles="@(MyAssemblies)"  
            <Output  
                TaskParameter="Assemblies"  
                ItemName="MyAssemblyIdentities"  
    </Target>  
  
</Project>  
```  
  
## Consulte também  
 [ \(tarefas\)](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)