---
title: T4 Diretiva de Assembly | Documentos do Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 4
author: alancameronwills
ms.author: awills
manager: douge
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 1405842233fdb9aceee50657f4c96ce06ef911d5
ms.lasthandoff: 02/22/2017

---
# <a name="t4-assembly-directive"></a>Diretiva de assembly T4
Em um modelo de texto de tempo de design do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], a diretiva `assembly` carrega um assembly de modo que seu código do modelo possa usar seus tipos. O efeito é semelhante ao de adicionar uma referência de assembly em um projeto do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 Para obter uma visão geral da gravação de modelos de texto, consulte [gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Você não precisa da diretiva `assembly` em um modelo de texto de tempo de execução (pré-processado). Em vez disso, adicione os assemblies necessários para o **referências** de seu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto.  
  
## <a name="using-the-assembly-directive"></a>Usando a diretiva de assembly  
 A sintaxe da diretiva é a seguinte:  
  
```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 O nome do assembly deve ser um dos seguintes:  
  
-   O nome forte do assembly no GAC, como `System.Xml.dll`. Você também pode usar o formato longo, como `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Para obter mais informações, consulte <xref:System.Reflection.AssemblyName>.</xref:System.Reflection.AssemblyName>  
  
-   O caminho absoluto do assembly  
  
 Você pode usar a sintaxe `$(variableName)` para referenciar variáveis do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], como `$(SolutionDir)`, e `%VariableName%` para referenciar variáveis de ambiente. Por exemplo:  
  
```  
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>  
```  
  
 A diretiva de assembly não tem nenhum efeito em um modelo de texto pré-processado. Em vez disso, inclui as referências necessárias no **referências** seção de seu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projeto. Para obter mais informações, consulte [geração de texto de tempo de execução com modelos de texto T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="standard-assemblies"></a>Assemblies padrão  
 Os seguintes assemblies são carregados automaticamente, de modo que não seja necessário gravar diretivas de assembly para eles:  
  
-   `Microsoft.VisualStudio.TextTemplating.1*.dll`  
  
-   `System.dll`  
  
-   `WindowsBase.dll`  
  
 Se você usar uma diretiva personalizada, o processador de diretriz pode carregar os assemblies adicionais. Por exemplo, se você gravar modelos para uma linguagem específica do domínio (DSL), você não precisa gravar diretivas de assembly para os assemblies a seguir:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`  
  
-   `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`  
  
-   O assembly que contém seu DSL.  
  
##  <a name="a-namemsbuilda-using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a>Usando propriedades do projeto no MSBuild e o Visual Studio  
 Macros do Visual Studio como $(SolutionDir) não funcionam no MSBuild. Se você quiser transformar modelos no computador de compilação, use as propriedades do projeto como alternativa.  
  
 Edite seu arquivo .csproj ou .vbproj para definir uma propriedade do projeto. Este exemplo define uma propriedade chamada `myLibFolder`:  
  
```xml  
<!-- Define a project property, myLibFolder: -->  
<PropertyGroup>  
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>  
</PropertyGroup>  
  
<!-- Tell the MSBuild T4 task to make the property available: -->  
<ItemGroup>  
    <T4ParameterValues Include="myLibFolder">  
      <Value>$(myLibFolder)</Value>  
    </T4ParameterValues>  
  </ItemGroup>  
  
```  
  
 Agora você pode usar a propriedade do projeto em modelos de texto, que se transformam corretamente no Visual Studio e no MSBuild:  
  
```  
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva de inclusão T4](../modeling/t4-include-directive.md)
