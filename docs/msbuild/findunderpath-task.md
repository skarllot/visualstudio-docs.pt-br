---
title: Tarefa FindUnderPath | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 26b60dd17f9090c5fe92697ebce0ee30dc0bc027
ms.lasthandoff: 02/22/2017

---
# <a name="findunderpath-task"></a>Tarefa FindUnderPath
Determina quais itens na coleção de itens especificados têm caminhos que estão dentro ou abaixo da pasta especificada.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `FindUnderPath`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`Files`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos cujos caminhos devem ser comparados com o caminho especificado pelo parâmetro `Path`.|  
|`InPath`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que foram encontrados no caminho especificado.|  
|`OutOfPath`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que não foram encontrados no caminho especificado.|  
|`Path`|Parâmetro obrigatório <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o caminho da pasta a ser usada como referência.|  
|`UpdateToAbsolutePaths`|Parâmetro `Boolean` opcional.<br /><br /> Se for verdadeiro, os caminhos dos itens de saída são atualizados para ser caminhos absolutos.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `FindUnderPath` para determinar se os arquivos contidos no item `MyFiles` têm caminhos existentes no caminho especificado pela propriedade `SearchPath`. Depois que a tarefa for concluída, o item `FilesNotFoundInPath` contém o arquivo `File1.txt` e o item `FilesFoundInPath` contém o arquivo `File2.txt`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
