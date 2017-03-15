---
title: Tarefa ResourcesGenerator | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
caps.latest.revision: 6
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
ms.openlocfilehash: a698aec32ff5ec093fe2cff2dc0533f6e364be21
ms.lasthandoff: 02/22/2017

---
# <a name="resourcesgenerator-task"></a>Tarefa ResourcesGenerator
A tarefa <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> insere um ou mais recursos (.jpg, .ico, .bmp, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] em formato binário e outros tipos de extensão) em um arquivo .resources.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`OutputPath`|Parâmetro obrigatório **String**.<br /><br /> Especifica o caminho do diretório de saída. Se o caminho não for um caminho absoluto, ele será tratado como um caminho relativo ao diretório do projeto raiz.|  
|`OutputResourcesFile`|Parâmetro de saída **ITaskItem[]** obrigatório.<br /><br /> Especifica o caminho e o nome dos arquivos .resource gerados. Se o caminho não for um caminho absoluto, o arquivo .resources será gerado em relação ao diretório raiz do projeto.|  
|`ResourcesFiles`|Parâmetro obrigatório **ITaskItem[]**.<br /><br /> Especifica um ou mais recursos para ser inserido no arquivo .resources gerado.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir gera um arquivo .resources com um único recurso .bmp. O recurso .bmp é gerado para um diretório relativo ao diretório raiz do projeto.  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também  
 [Referência MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Compilando um aplicativo WPF (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
