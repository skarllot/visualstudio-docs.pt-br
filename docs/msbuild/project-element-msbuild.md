---
title: Elemento Project (MSBuild) | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
caps.latest.revision: 31
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
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: 224371f6915258a9860c5f05554445f6b1ae106c
ms.lasthandoff: 03/01/2017

---
# <a name="project-element-msbuild"></a>Elemento Project (MSBuild)
Elemento raiz necessário de um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

## <a name="syntax"></a>Sintaxe  

```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  

## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  

### <a name="attributes"></a>Atributos  

|Atributo|Descrição|  
|---------------|-----------------|  
|`DefaultTargets`|Atributo opcional.<br /><br /> Os destinos padrão serão o ponto de entrada do build se nenhum destino for especificado. Vários destinos são separados por ponto e vírgula (;).<br /><br /> Se nenhum destino padrão for especificado no atributo `DefaultTargets` ou na linha de comando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], o mecanismo executa o primeiro destino no arquivo de projeto após os elementos [Import](../msbuild/import-element-msbuild.md) serem avaliados.|  
|`InitialTargets`|Atributo opcional.<br /><br /> Os destinos iniciais serão executados antes dos destinos especificados no atributo `DefaultTargets` ou na linha de comando. Vários destinos são separados por ponto e vírgula (;).|  
|`SDK`|Atributo opcional. (Disponível somente para projetos do .NET Core no Visual Studio 2017 ou posterior.)<br /><br /> A versão do SDK a ser usada para criar instruções Import implícitas adicionadas ao arquivo .proj. Por exemplo, `<Project Sdk="Microsoft.NET.Sdk/1.0.0-RC" />`.|  
|`ToolsVersion`|Atributo opcional.<br /><br /> A versão do conjunto de ferramentas MSBuild usada para determinar os valores para $(MSBuildBinPath) e $(MSBuildToolsPath).|  
|`TreatAsLocalProperty`|Atributo opcional.<br /><br /> Nomes de propriedade não serão considerados globais. Esse atributo impede que as propriedades específicas de linha de comando substituam valores de propriedade definidos em um arquivo de projeto ou destinos e todas as importações subsequentes. Várias propriedades são separadas por ponto e vírgula (;).<br /><br /> Normalmente, propriedades globais substituem os valores de propriedade que são definidos no arquivo de projeto ou destinos. Se a propriedade está listada no valor `TreatAsLocalProperty`, o valor da propriedade global não substitui os valores de propriedade definidos no arquivo e as importações subsequentes. Para obter mais informações, consulte [Como compilar os mesmos arquivos de origem com opções diferentes](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Observação:** defina as propriedades globais no prompt de comando usando a opção **/property** (ou **/p**). Você também pode definir ou modificar as propriedades globais para projetos filho em um build de vários projetos usando o atributo `Properties` da tarefa MSBuild. Para mais informações, consulte [Tarefa do MSBuild](../msbuild/msbuild-task.md).|  
|`Xmlns`|Atributo opcional.<br /><br /> Quando for especificado, o atributo `xmlns` deve ter o valor de “http://schemas.microsoft.com/developer/msbuild/2003”.|  

### <a name="child-elements"></a>Elementos filho  

|Elemento|Descrição|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Elemento opcional.<br /><br /> Avalia a elementos filho para selecionar um conjunto de elementos `ItemGroup` e/ou `PropertyGroup` a ser avaliado.|  
|[Import](../msbuild/import-element-msbuild.md)|Elemento opcional.<br /><br /> Permite que um arquivo de projeto importe outro arquivo de projeto. Pode ser que não haja nenhum ou mais de um elemento `Import` em um projeto.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Elemento opcional.<br /><br /> Um elemento de agrupamento para itens individuais. Itens são especificados usando o elemento [Item](../msbuild/item-element-msbuild.md). Pode ser que não haja nenhum ou mais de um elemento `ItemGroup` em um projeto.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Elemento opcional.<br /><br /> Fornece uma maneira de manter informações não [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] em um arquivo de projeto [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Pode ser que não haja nenhum ou um elemento `ProjectExtensions` em um projeto.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Elemento opcional.<br /><br /> Um elemento de agrupamento para propriedades individuais. Propriedades são especificadas usando o elemento [Property](../msbuild/property-element-msbuild.md). Pode ser que não haja nenhum ou mais de um elemento `PropertyGroup` em um projeto.|  
|[Target](../msbuild/target-element-msbuild.md)|Elemento opcional.<br /><br /> Contém um conjunto de tarefas para [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] executar em sequência. Tarefas são especificadas usando o elemento [Task](../msbuild/task-element-msbuild.md). Pode ser que não haja nenhum ou mais de um elemento `Target` em um projeto.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Elemento opcional.<br /><br /> Fornece uma maneira para registrar tarefas em [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Pode ser que não haja nenhum ou mais de um elemento `UsingTask` em um projeto.|  

### <a name="parent-elements"></a>Elementos pai  
 nenhuma.  

## <a name="see-also"></a>Consulte também  
 [Como especificar o destino a ser compilado primeiro](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Referência de linha de comando](../msbuild/msbuild-command-line-reference.md)   
 [Referência do esquema de arquivos de projeto](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)

