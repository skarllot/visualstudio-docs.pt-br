---
title: Tarefa GetWinFXPath | Microsoft Docs
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
- getting the directory of the current .NET Framework runtime [WPF MSBuild]
- GetWinFXPath task [WPF MSBuild], parameters
- GetWinFXPath task [WPF MSBuild]
- obtaining the path to the current .NET Framework runtime [WPF MSBuild]
ms.assetid: b1dfb467-f3d3-47f3-83ef-af7b0e33a772
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 3d32d11a430227800cb3ed53831a9565eb6adeb3
ms.openlocfilehash: a860a2bf2fe61f16e5e18a85fdd71e57de5188f1
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---
# <a name="getwinfxpath-task"></a>Tarefa GetWinFXPath
A tarefa <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> retorna o diretório do tempo de execução [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] atual.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`WinFXPath`|Parâmetro de saída opcional **String**.<br /><br /> Especifica o caminho real para o tempo de execução de [!INCLUDE[TLA2#tla_winfx](../msbuild/includes/tla2sharptla_winfx_md.md)].|  
|`WinFXNativePath`|Parâmetro obrigatório **String**.<br /><br /> Especifica o caminho para o tempo de execução de [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)] nativo.|  
|`WinFXWowPath`|Parâmetro obrigatório **String**.<br /><br /> Especifica o caminho para os assemblies de [!INCLUDE[TLA#tla_winfx](../msbuild/includes/tlasharptla_winfx_md.md)] no módulo **Windows on Windows** de 32 bits em sistemas de 64 bits.|  
  
## <a name="remarks"></a>Comentários  
 Se a tarefa <xref:Microsoft.Build.Tasks.Windows.GetWinFXPath> está em execução em um processador de 64 bits, o parâmetro **WinFXPath** está definido como o caminho armazenado no parâmetro **WinFXWowPath**, caso contrário, o parâmetro **WinFXPath** é definido como o caminho armazenado no parâmetro **WinFXNativePath**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a tarefa **GetWinFXPath** para detectar o caminho nativo para o tempo de execução de [!INCLUDE[TLA2#tla_titlewinfx](../msbuild/includes/tla2sharptla_titlewinfx_md.md)].  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também  
 [Referência MSBuild do WPF](../msbuild/wpf-msbuild-reference.md)   
 [Referência de tarefas](../msbuild/wpf-msbuild-task-reference.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Como compilar um aplicativo WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
