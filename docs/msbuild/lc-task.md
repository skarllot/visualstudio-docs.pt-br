---
title: Tarefa LC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
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
ms.openlocfilehash: 7b4ae3bba069cb1218b4ff1cf0b78877d10dfd34
ms.lasthandoff: 02/22/2017

---
# <a name="lc-task"></a>Tarefa LC
Encapsula LC.exe, que gera um arquivo .license de um arquivo .licx. Para obter mais informações sobre LC.exe, consulte [Lc.exe (Compilador de Licença)](http://msdn.microsoft.com/Library/2de803b8-495e-4982-b209-19a72aba0460).  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `LC`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`LicenseTarget`|Parâmetro obrigatório <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o executável para o qual os arquivos .licenses são gerados.|  
|`NoLogo`|Parâmetro `Boolean` opcional.<br /><br /> Suprime a exibição do banner de inicialização da Microsoft.|  
|`OutputDirectory`|Parâmetro `String` opcional.<br /><br /> Especifica o diretório no qual os arquivos .licenses de saída devem ser colocados.|  
|`OutputLicense`|Parâmetro de saída opcional <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica o nome do arquivo .licenses. Se você não especificar um nome, o nome do arquivo .licx será usado e o arquivo .licenses será colocado no diretório contendo o arquivo .licx.|  
|`ReferencedAssemblies`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os componentes referenciados a carregar ao gerar o arquivo .license.|  
|`SdkToolsPath`|Parâmetro `String` opcional.<br /><br /> Especifica o caminho para as ferramentas do SDK, por exemplo, resgen.exe.|  
|`Sources`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os itens contendo os componentes licenciados para incluir no arquivo .licenses. Para obter mais informações, consulte a documentação da opção `/complist` em [Lc.exe (Compilador de Licença)](http://msdn.microsoft.com/Library/2de803b8-495e-4982-b209-19a72aba0460).|  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que, por sua vez, herda da classe <xref:Microsoft.Build.Utilities.ToolTask>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base ToolTaskExtension](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `LC` para compilar licenças.  
  
```xml  
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
  
## <a name="see-also"></a>Consulte também  
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)
