---
title: Arquivos .targets do MSBuild | Microsoft Docs
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
- .Targets files
- MSBuild, .Targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
caps.latest.revision: 17
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
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: e47709e23ae963a9339499eb1b1e1d28834be5bf

---
# <a name="msbuild-targets-files"></a>Arquivos .targets do MSBuild
O [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] inclui vários arquivos .targets que contêm itens, propriedades, destinos e tarefas para cenários comuns. Esses arquivos são automaticamente importados para a maioria dos arquivos de projeto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para simplificar a manutenção e a legibilidade.  
  
 Os projetos normalmente importam um ou mais arquivos .targets para definir o processo de build. Por exemplo, um projeto [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] criado pelo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importará Microsoft.CSharp.targets que importa Microsoft.Common.targets. O próprio projeto [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] definirá os itens e propriedades específicos para esse projeto, mas as regras de build padrão para um projeto [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] são definidas pelos arquivos .targets importados.  
  
 O valor `$(MSBuildToolsPath)` especifica o caminho desses arquivos .targets comuns. Se o `ToolsVersion` for 4.0, os arquivos estarão no seguinte local: `WindowsInstallationPath\Microsoft.NET\Framework\v4.0.30319\`  
  
> [!NOTE]
>  Para obter informações sobre como criar seus próprios destinos, consulte [Destinos](../msbuild/msbuild-targets.md). Para obter informações sobre como usar o elemento `Import` para inserir um arquivo de projeto em outro arquivo de projeto, consulte [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) e [Como usar o mesmo destino em vários arquivos de projeto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).  
  
## <a name="common-targets-files"></a>Arquivos .targets comuns  
  
|Arquivo .targets|Descrição|  
|-------------------|-----------------|  
|Microsoft.Common.targets|Define as etapas no processo de build padrão de projetos [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].<br /><br /> Importado pelos arquivos Microsoft.CSharp.targets e Microsoft.VisualBasic.targets, quem incluem as seguintes instruções: `<Import Project="Microsoft.Common.targets" />`|  
|Microsoft.CSharp.targets|Define as etapas no processo de build padrão de projetos do Visual C#.<br /><br /> Importado pelos arquivos de projeto do Visual C# (.csproj), que incluem a seguinte instrução: `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`|  
|Microsoft.VisualBasic.targets|Define as etapas no processo de build padrão de projetos do Visual Basic.<br /><br /> Importado pelos arquivos de projeto do Visual Basic (.vbproj), que incluem a seguinte instrução: `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`|  
  
## <a name="see-also"></a>Consulte também  
 [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Referência do MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](../msbuild/msbuild.md)


<!--HONumber=Feb17_HO4-->


