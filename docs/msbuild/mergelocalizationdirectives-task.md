---
title: Tarefa MergeLocalizationDirectives | Microsoft Docs
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
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
caps.latest.revision: 5
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
ms.openlocfilehash: 94cd8bfa5807e46025f416ad87fc9d82990ef966
ms.lasthandoff: 02/22/2017

---
# <a name="mergelocalizationdirectives-task"></a>Tarefa MergeLocalizationDirectives
A tarefa <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> mescla os atributos de localização e comentários de um ou mais arquivos de formato binário [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] em um único arquivo para todo o assembly.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`GeneratedLocalizationFiles`|Parâmetro obrigatório **ITaskItem[]**.<br /><br /> Especifica a lista de arquivos de diretivas de localização de arquivos individuais no formato binário [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputFile`|Parâmetro de saída da **cadeia de caracteres** necessário.<br /><br /> Especifica o caminho de saída do assembly de diretivas de localização compilado.|  
  
## <a name="remarks"></a>Comentários  
 Você pode adicionar atributos de localização e comentários no conteúdo [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)]. Com suporte à localização da [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)], você pode retirar os comentários e atributos de localização e colocá-los em um arquivo .loc separado do assembly gerado. Você pode fazer isso usando o atributo **LocalizationPropertyStorage**. Para obter mais informações sobre os atributos de localização e comentários e **LocalizationPropertyStorage**, confira [Atributos de localização e comentários](http://msdn.microsoft.com/Library/ead2d9ac-b709-4ec1-a924-39927a29d02f).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mescla os comentários de localização de vários arquivos de formato binário [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] em um único arquivo .loc.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MergeLocalizationDirectivesTask">  
    <MergeLocalizationDirectives   
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"  
      OutputFile="obj\debug\WPFMSBuildSample.loc" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Referência MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Como compilar um aplicativo WPF (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
